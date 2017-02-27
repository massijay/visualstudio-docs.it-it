---
title: "ActivityDesigner ExistsInCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ExistsInCollection`1.UI"
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ActivityDesigner ExistsInCollection&lt;T&gt;
L'ActivityDesigner **ExistsInCollection\<T\>** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.ExistsInCollection%601>.  
  
## Attività ExistsInCollection\<T\>  
 L'attività <xref:System.Activities.Statements.ExistsInCollection%601> determina se in una particolare raccolta è presente un elemento specificato.  
  
### Utilizzo dell'ActivityDesigner ExistsInCollection\<T\>  
 L'ActivityDesigner **ExistsInCollection\<T\>** è disponibile nella categoria **Raccolta** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **ExistsInCollection\<T\>** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.ExistsInCollection%601> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito ExistsInCollection\<Int32\>.Per impostazione predefinita, *TypeArgument* è **Int32**.Tale valore può essere modificato nella griglia delle proprietà.  È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **ExistsInCollection\<T\>** o nella casella **DisplayName** della griglia delle proprietà.Le altre proprietà devono essere modificate nella griglia delle proprietà.  
  
### Proprietà di ExistsInCollection\<T\>  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ExistsInCollection%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ExistsInCollection%601>.Il valore predefinito è ExistsInCollection\<Int32\>.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Elemento da aggiungere a Collection\<T\>.Questo elemento è di tipo *T*, che è di tipo *TypeArgument*.Per specificare l'elemento, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|Raccolta alla quale aggiungere l'elemento.Questa raccolta è di tipo **ICollection\<TypeArgument\>.** Per specificarla, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|*TypeArgument*|True|Tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>.Per impostazione predefinita, questo tipo *TypeArgument* è impostato su **Int32**.Per cambiare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Valore che indica se l'elemento specificato è presente nella raccolta.Per specificare una variabile da associare al risultato, digitare una variabile Visual Basic nella griglia delle proprietà.|  
  
## Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)