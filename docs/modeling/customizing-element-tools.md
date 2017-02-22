---
title: "Personalizzazione di strumenti elemento | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
caps.handback.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Personalizzazione di strumenti elemento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In alcune definizioni DSL, si rappresenta un singolo concetto come un gruppo di elementi. Ad esempio, se si crea un modello in cui un componente dispone di un set fisso di porte, si desidera sempre le porte da creare contemporaneamente il proprio componente padre. Pertanto, è necessario personalizzare lo strumento di creazione di elemento in modo che crei un gruppo di elementi anziché di uno. A tale scopo, è possibile personalizzare come viene inizializzato lo strumento di creazione di elemento.  
  
 È inoltre possibile sostituire cosa accade quando lo strumento viene trascinato nel diagramma o un elemento.  
  
## La personalizzazione del contenuto di uno strumento elemento  
 Ogni strumento elemento archivia un'istanza di un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\), che contiene una versione serializzata di una o più elementi del modello e i collegamenti. Per impostazione predefinita, EGP di uno strumento elemento contiene un'istanza della classe specificato per lo strumento. È possibile modificare questa impostazione viene sottoposto a override *Linguaggioutente*`ToolboxHelper.CreateElementToolPrototype`. Questo metodo viene chiamato quando viene caricato il pacchetto DSL.  
  
 Un parametro del metodo è l'ID della classe specificata nella definizione DSL. Quando viene chiamato il metodo con la classe che si è interessati, è possibile aggiungere elementi aggiuntivi nel EGP.  
  
 Deve includere il EGP incorporare collegamenti da un elemento principale per gli elementi sussidiari. È inoltre possibile utilizzare i collegamenti di riferimento.  
  
 Nell'esempio seguente viene creato un elemento principale e due elementi incorporati. La classe principale viene chiamata resistenza e dispone di due relazioni di incorporamento per gli elementi denominati Terminal. Le proprietà del ruolo incorporamento sono denominate Terminal1 e Terminal2 ed entrambi hanno una molteplicità di 1..1.  
  
```  
using Microsoft.VisualStudio.Modeling; ...    
public partial class CircuitDiagramToolboxHelper  
{  
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)  
  {  
    // A case for each tool to customize:    
    if (domainClassId == Resistor.DomainClassId)  
    {  
      // Set up the prototype elements and links:  
      Resistor resistor = new Resistor(store);  
      resistor.Terminal1 = new Terminal(store);   
      resistor.Terminal2 = new Terminal(store);  
      resistor.Terminal1.Name = "T1"; // embedding  
      resistor.Terminal2.Name = "T2"; // embedding  
      // We could also set up reference links.  
  
      // Create an element group prototype for the toolbox:  
      ElementGroup egp = new ElementGroup(store.DefaultPartition);  
      egp.AddGraph(resistor, true);  
      // We do not have to explicitly include embedded children.  
      return egp.CreatePrototype();  
    }  
    // Element tools for other classes:  
    else  
      return base.CreateElementToolPrototype(store, domainClassId);  
  }  
}  
```  
  
## Vedere anche  
 [Personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md)