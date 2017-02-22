---
title: "Procedura: estendere la finestra di progettazione di linguaggio specifico di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 9
caps.handback.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Procedura: estendere la finestra di progettazione di linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare estensioni per la finestra di progettazione che consente di modificare le definizioni DSL. Tipi di estensione che è possibile apportare includono l'aggiunta di comandi di menu, aggiunta di gestori per trascinano e fare doppio clic su movimenti e le regole vengono attivate quando modificare determinati tipi di valori o relazioni. Le estensioni possono essere fornite come Visual Studio Integration Extension \(VSIX\) e distribuite agli altri utenti.  
  
 Per ulteriori informazioni su questa funzionalità, il codice di esempio di Visual Studio vedere [Visualization and Modeling SDK \(VMSDK\) sito Web](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
## Impostazione della soluzione  
 Consente di impostare un progetto che contiene il codice dell'estensione e un progetto VSIX che esporta il progetto. La soluzione può contenere altri progetti che vengono incorporate nella stessa estensione VSIX.  
  
#### Per creare una soluzione di estensione di progettazione DSL  
  
1.  Creare un nuovo progetto utilizzando il modello di progetto libreria di classi. Nel **Nuovo progetto** la finestra di dialogo, fare clic su **Visual c\#** e nella finestra centrale fare clic su **libreria di classi**.  
  
     Questo progetto conterrà il codice delle estensioni.  
  
2.  Creare un nuovo progetto utilizzando il modello di progetto VSIX. Nel **Nuovo progetto** finestra di dialogo espandere **Visual c\#**, fare clic su **estendibilità**, e quindi nella finestra centrale selezionare **progetto VSIX**.  
  
     Selezionare **aggiungere alla soluzione**.  
  
     Source.Extension.vsixmanifest verrà aperto nell'editor del manifesto VSIX.  
  
3.  Sopra il campo del contenuto, fare clic su **Aggiungi contenuto**.  
  
4.  Nel **Aggiungi contenuto** la finestra di dialogo, impostare **Selezionare un tipo di contenuto** a **componente MEF**, e impostare **progetto** al progetto libreria di classi.  
  
5.  Fare clic su **Seleziona versioni** e verificare che **Visual Studio Enterprise** sia selezionata.  
  
6.  Assicurarsi che il progetto VSIX sia il progetto di avvio della soluzione.  
  
7.  Nel progetto libreria di classi, aggiungere riferimenti agli assembly seguenti:  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## Testing e distribuzione  
 Per testare qualsiasi delle estensioni in questo argomento, compilare ed eseguire la soluzione. Viene aperta un'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In questo caso, aprire una soluzione DSL. Modificare il diagramma DslDefinition. Il comportamento dell'estensione può essere visualizzato.  
  
 Per distribuire le estensioni principale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], e in altri computer, seguire questi passaggi:  
  
1.  Trovare il file di installazione di VSIX, nel progetto VSIX in bin\\\*\\\*.vsix  
  
2.  Copiare questo file nel computer di destinazione e quindi in Esplora risorse \(o Esplora File\), fare doppio clic.  
  
     Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà aperto Gestione estensioni per verificare che sia stato installato l'estensione.  
  
 Per disinstallare l'estensione, seguire questi passaggi:  
  
1.  in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], via il **strumenti** menu, fare clic su **Gestione estensioni**.  
  
2.  Selezionare l'estensione ed eliminarlo.  
  
## Aggiunta di un comando di Menu di scelta rapida  
 Per visualizzare un comando di menu di scelta rapida nell'area di progettazione DSL o nella finestra Esplora DSL, scrivere una classe simile al seguente.  
  
 La classe deve implementare `ICommandExtension` e deve avere l'attributo `DslDefinitionModelCommandExtension`.  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## Gestisce i movimenti del Mouse  
 Il codice è simile al codice del comando di menu.  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## Rispondere alle modifiche ai valori  
 Questo gestore ha bisogno di un modello di dominio funzioni correttamente. Offriamo un modello di dominio semplice.  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 Il codice seguente implementa un modello semplice. Creare un nuovo GUID per sostituire il segnaposto.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```