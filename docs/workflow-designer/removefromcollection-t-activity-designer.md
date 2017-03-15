---
title: "ActivityDesigner RemoveFromCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.RemoveFromCollection`1.UI"
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ActivityDesigner RemoveFromCollection&lt;T&gt;
L'ActivityDesigner **RemoveFromCollection\<T\>** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.RemoveFromCollection%601>.  
  
## Attività RemoveFromCollection\<T\>  
 L'attività <xref:System.Activities.Statements.RemoveFromCollection%601> rimuove un determinato elemento da una raccolta specifica.  
  
### Utilizzo dell'ActivityDesigner RemoveFromCollection\<T\>  
 L'ActivityDesigner **RemoveFromCollection\<T\>** è disponibile nella categoria **Raccolta** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **RemoveFromCollection\<T\>** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.RemoveFromCollection%601> con la proprietà  <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito RemoveFromCollection\<Int32\>.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **RemoveFromCollection\<T\>** o nella casella **DisplayName** della griglia delle proprietà.Le altre proprietà devono essere modificate nella griglia delle proprietà.  
  
### Proprietà di RemoveFromCollection\<T\>  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.RemoveFromCollection%601> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.RemoveFromCollection%601>.Il valore predefinito è RemoveFromCollection\<Int32\>.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|Elemento da aggiungere a **Collection\<T\>**.Questo elemento è di tipo *T* che, a sua volta, è di tipo *TypeArgument*.Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento.Questa raccolta è di tipo **ICollection\<TypeArgument\>.** Per specificarla, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>.Per impostazione predefinita, questo tipo *TypeArgument* è impostato su **Int32**.Per cambiare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è stato rimosso dalla raccolta.Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|  
  
## Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)