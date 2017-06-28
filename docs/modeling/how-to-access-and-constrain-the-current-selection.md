---
title: "Procedura: accedere e vincolare la selezione corrente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, accesso alla selezione corrente"
ms.assetid: 2990981e-dfae-416f-b0d0-7197f1242dfa
caps.latest.revision: 14
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 14
---
# Procedura: accedere e vincolare la selezione corrente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si scrive un gestore comandi o movimenti per il linguaggio specifico di dominio, è possibile determinare quale elemento utente selezionata. È possibile inoltre impedire alcune forme o i campi selezionati. Ad esempio, è possibile disporre che, quando l'utente fa clic su un elemento decorator icona, viene selezionata invece la forma che lo contiene. Vincolare la selezione in questo modo riduce il numero di gestori che è necessario scrivere. Inoltre rende più semplice per l'utente, che è possibile fare clic su un punto qualsiasi nella forma senza la necessità di evitare l'elemento decorator.  
  
## Accesso alla selezione corrente da un gestore del comando  
 La classe di set di comandi per un linguaggio specifico di dominio contiene i gestori di comando per i comandi personalizzati. La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe da cui deriva la classe di set di comandi per un linguaggio specifico di dominio, fornisce alcuni membri per l'accesso alla selezione corrente.  
  
 A seconda del comando, il gestore del comando potrebbe essere la selezione in Progettazione modelli, in Esplora modelli o la finestra attiva.  
  
#### Per accedere alle informazioni di selezione  
  
1.  La <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe definisce i membri seguenti che possono essere utilizzati per accedere alla selezione corrente.  
  
    |Membro|Descrizione|  
    |------------|-----------------|  
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A>|Restituisce `true` Se uno degli elementi selezionati nella finestra di progettazione del modello è una forma raggruppamento; in caso contrario, `false`.|  
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A>|Restituisce `true` Se il diagramma è selezionata nella finestra di progettazione del modello; in caso contrario, `false`.|  
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A>|Restituisce `true` Se esattamente un elemento è selezionato nella finestra di progettazione del modello; in caso contrario, `false`.|  
    |Metodo <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A>|Restituisce `true` Se esattamente un elemento è selezionato nella finestra attiva; in caso contrario, `false`.|  
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A>|Ottiene una raccolta di sola lettura degli elementi selezionati nella finestra di progettazione del modello.|  
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A>|Ottiene una raccolta di sola lettura degli elementi selezionati nella finestra attiva.|  
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A>|Ottiene l'elemento principale della selezione in Progettazione modelli.|  
    |Proprietà <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A>|Ottiene l'elemento principale della selezione nella finestra attiva.|  
  
2.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A> proprietà della <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe fornisce l'accesso a di <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> oggetto che rappresenta la finestra di progettazione del modello e fornisce accesso aggiuntivo gli elementi selezionati nella finestra di progettazione del modello.  
  
3.  Inoltre, il codice generato definisce una proprietà di finestra strumento di Esplora risorse e una proprietà di selezione Esplora nel comando set \(classe\) per il linguaggio specifico di dominio.  
  
    -   La proprietà della finestra dello strumento explorer restituisce un'istanza della classe della finestra Esplora strumento per il linguaggio specifico di dominio. Classe della finestra dello strumento explorer deriva la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> classe e rappresenta Esplora modelli per il linguaggio specifico di dominio.  
  
    -   Il `ExplorerSelection` proprietà restituisce l'elemento selezionato nella finestra di Esplora modelli per il linguaggio specifico di dominio.  
  
## Determinare quale finestra è attiva  
 Il <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> contiene interfaccia definisce i membri che forniscono l'accesso allo stato di selezione corrente nella shell. È possibile ottenere un <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> oggetto di classe del pacchetto o la classe di set di comandi per il linguaggio specifico di dominio tramite il `MonitorSelection` definita nella classe di base di ogni proprietà. Deriva la classe del pacchetto la <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> classe e la classe di set di comandi deriva la <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe.  
  
#### Per determinare da un gestore del comando, il tipo di finestra è attivo  
  
1.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A> proprietà della <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> classe restituisce un' <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> oggetto che fornisce accesso allo stato di selezione corrente nella shell.  
  
2.  Il <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A> di proprietà di <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> interfaccia ottiene il contenitore di selezione attiva, che può essere diverso dalla finestra attiva.  
  
3.  Aggiungere che le seguenti proprietà per il comando set \(classe\) è il linguaggio specifico di dominio per determinare il tipo di finestra è attivo.  
  
    ```c#  
    // using Microsoft.VisualStudio.Modeling.Shell;  
  
    // Returns true if the model designer is the active selection container;  
    // otherwise, false.  
    protected bool IsDesignerActive  
    {  
        get  
        {  
            return (this.MonitorSelection.CurrentSelectionContainer  
                is DiagramDocView);  
        }  
    }  
  
    // Returns true if the model explorer is the active selection container;  
    // otherwise, false.  
    protected bool IsExplorerActive  
    {  
        get  
        {  
            return (this.MonitorSelection.CurrentSelectionContainer  
                is ModelExplorerToolWindow);  
        }  
    }  
    ```  
  
## Vincolare la selezione  
 L'aggiunta di regole di selezione, è possibile controllare quali elementi sono selezionati quando l'utente seleziona un elemento del modello. Per consentire all'utente di considerare un numero di elementi come una singola unità, ad esempio, è possibile utilizzare una regola di selezione.  
  
#### Per creare una regola di selezione  
  
1.  Creare un file di codice personalizzato nel progetto DSL  
  
2.  Definire una classe di regola di selezione che è derivata dalla <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> classe.  
  
3.  Eseguire l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> metodo della classe di regola di selezione per applicare i criteri di selezione.  
  
4.  Aggiungere una definizione di classe parziale per la classe ClassDiagram al file di codice personalizzato.  
  
     La `ClassDiagram` classe deriva dalla <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> classe e viene definito nel file di codice generato, Diagram.cs, nel progetto DSL.  
  
5.  Eseguire l'override di <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> proprietà della `ClassDiagram` classe per restituire la regola di selezione personalizzata.  
  
     L'implementazione predefinita della <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> proprietà ottiene un oggetto regola di selezione che non modifica la selezione.  
  
### Esempio  
 Il file di codice seguente crea una regola di selezione che si espande la selezione per includere tutte le istanze di ciascuna delle forme dominio che è stato inizialmente selezionato.  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
namespace CompanyName.ProductName.GroupingDsl  
{  
    public class CustomSelectionRules : DiagramSelectionRules  
    {  
        protected Diagram diagram;  
        protected IElementDirectory elementDirectory;  
  
        public CustomSelectionRules(Diagram diagram)  
        {  
            if (diagram == null) throw new ArgumentNullException();  
  
            this.diagram = diagram;  
            this.elementDirectory = diagram.Store.ElementDirectory;  
        }  
  
        /// <summary>Called by the design surface to allow selection filtering.  
        /// </summary>  
        /// <param name="currentSelection">[in] The current selection before any  
        /// ShapeElements are added or removed.</param>  
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to  
        /// be added to the selection.</param>  
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems  
        /// to be removed from the selection.</param>  
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become  
        /// the primary DiagramItem of the selection. A null value signifies that  
        /// the last DiagramItem in the resultant selection should be assumed as  
        /// the primary DiagramItem.</param>  
        /// <returns>true if some or all of the selection was accepted; false if  
        /// the entire selection proposal was rejected. If false, appropriate  
        /// feedback will be given to the user to indicate that the selection was  
        /// rejected.</returns>  
        public override bool GetCompliantSelection(  
            SelectedShapesCollection currentSelection,  
            DiagramItemCollection proposedItemsToAdd,  
            DiagramItemCollection proposedItemsToRemove,  
            DiagramItem primaryItem)  
        {  
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;  
  
            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();  
  
            foreach (DiagramItem item in proposedItemsToAdd)  
            {  
                if (item.Shape != null)  
                    itemsToAdd.Add(item.Shape.GetDomainClass());  
            }  
            proposedItemsToAdd.Clear();  
            foreach (DomainClassInfo classInfo in itemsToAdd)  
            {  
                foreach (ModelElement element  
                    in this.elementDirectory.FindElements(classInfo, false))  
                {  
                    if (element is ShapeElement)  
                    {  
                        proposedItemsToAdd.Add(  
                            new DiagramItem((ShapeElement)element));  
                    }  
                }  
            }  
  
            return true;  
        }  
    }  
  
    public partial class ClassDiagram  
    {  
        protected CustomSelectionRules customSelectionRules = null;  
  
        protected bool multipleSelectionMode = true;  
  
        public override DiagramSelectionRules SelectionRules  
        {  
            get  
            {  
                if (multipleSelectionMode)  
                {  
                    if (customSelectionRules == null)  
                    {  
                        customSelectionRules = new CustomSelectionRules(this);  
                    }  
                    return customSelectionRules;  
                }  
                else  
                {  
                    return base.SelectionRules;  
                }  
            }  
        }  
    }  
}  
```  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>   
 <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>   
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>