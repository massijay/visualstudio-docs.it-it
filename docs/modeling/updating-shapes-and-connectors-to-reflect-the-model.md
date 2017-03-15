---
title: Aggiornamento di forme e connettori per riflettere il modello | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 97ec749c0a89dae6c5a98702926d8ad82b6af3ac
ms.lasthandoff: 02/22/2017

---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Aggiornamento di forme e di connettori per riflettere il modello
In un linguaggio specifico di dominio in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile rendere l'aspetto di una forma riflette lo stato del modello sottostante.  
  
 Gli esempi di codice in questo argomento devono essere aggiunto a un `.cs` file di `Dsl` progetto. È necessario che queste istruzioni in ogni file:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Impostare le proprietà di mappa di forme per controllare la visibilità di un elemento decorator  
 È possibile controllare la visibilità di un elemento decorator senza scrivere codice programma, configurando il mapping tra la forma e la classe di dominio nella definizione DSL. Per ulteriori informazioni, vedere  [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Esporre il colore e stile di una forma come proprietà  
 Nella definizione DSL, fare clic su classe shape, scegliere **Aggiungi esposta**, quindi fare clic su uno degli elementi, ad esempio **colore riempimento**.  
  
 La forma ha ora una proprietà di dominio che è possibile impostare nel codice programma o come un utente. Per impostarla nel codice del programma di un comando o una regola, ad esempio, è possibile scrivere:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Se si desidera rendere la variabile di proprietà solo in controllo del programma e non dall'utente, selezionare la nuova proprietà di dominio, ad esempio **colore riempimento** nel diagramma di definizione DSL. Quindi, nella finestra Proprietà impostare **è esplorabile** a `false` o impostare **è Readonly dell'interfaccia utente** a `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definire le regole di modifica per colore, stile o il percorso dipende dalla proprietà elemento modello  
 È possibile definire regole che aggiornano l'aspetto della forma dipendente da altre parti del modello. Ad esempio, è possibile definire una regola di modifica su un elemento del modello che aggiorna il colore della forma dipende dalla proprietà dell'elemento del modello. Per ulteriori informazioni sulle regole di modifica, vedere [propagare le modifiche all'interno di modello delle regole](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Utilizzare le regole solo per aggiornare le proprietà che vengono mantenute all'interno dell'archivio, poiché le regole non vengono richiamate quando viene eseguito il comando Annulla. Non include alcune funzionalità grafiche, ad esempio le dimensioni e la visibilità di una forma. Per aggiornare le funzionalità di una forma, vedere [le funzionalità di aggiornamento dell'archivio Non grafica](#OnAssociatedProperty).  
  
 Nell'esempio seguente si presuppone che sia stata esposta `FillColor` come una proprietà di dominio come descritto nella sezione precedente.  
  
```c#  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Utilizzare OnChildConfigured per inizializzare le proprietà della forma  
 Per impostare le proprietà di una forma quando viene inizialmente creata, la sostituzione `OnChildConfigured()` in una definizione parziale della classe diagramma. Il diagramma è specificato nella definizione DSL e il codice generato è **Dsl\Generated Code\Diagram.cs**. Ad esempio:  
  
```c#  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 Questo metodo può essere utilizzato sia per le funzionalità di archivio non, ad esempio la dimensione della forma e le proprietà del dominio.  
  
##  <a name="a-nameonassociatedpropertya-use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a>Utilizzare AssociateValueWith() per aggiornare altre funzionalità di una forma  
 Per alcune funzionalità di una forma, ad esempio se dispone di un'ombreggiatura o lo stile della freccia del connettore, non esiste alcun metodo incorporato di esporre la funzionalità come una proprietà di dominio.  Modifiche a tali funzionalità non sono sotto il controllo del sistema di transazione. Pertanto, non è appropriato per aggiornarli utilizzando le regole, perché le regole non vengono richiamate quando l'utente esegue il comando Annulla.  
  
 In alternativa, è possibile aggiornare tali funzionalità tramite <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>.</xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> Nell'esempio seguente, lo stile della freccia del connettore è controllato da un valore della proprietà del dominio nella relazione che consente di visualizzare il connettore:  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape’s built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`deve essere chiamato una volta per ogni proprietà di dominio che si desidera registrare. Dopo che è stato chiamato, tutte le modifiche alla proprietà specificata chiamerà `OnAssociatedPropertyChanged()` in tutte le forme che presentano l'elemento del modello della proprietà.  
  
 Non è necessario chiamare `AssociateValueWith()` per ogni istanza. Anche se InitializeResources è un metodo di istanza, viene richiamato solo una volta per ogni classe della forma.

