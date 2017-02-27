---
title: "ActivityDesigner ClearCollection&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ActivityDesigner ClearCollection&lt;T&gt;
L'ActivityDesigner **ClearCollection\<T\>** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.ClearCollection%601>.  
  
## Attività ClearCollection\<T\>  
 L'attività <xref:System.Activities.Statements.ClearCollection%601> cancella tutti gli elementi di una raccolta specificata.  
  
### Utilizzo dell'ActivityDesigner ClearCollection\<T\>  
 L'ActivityDesigner **ClearCollection\<T\>** è disponibile nella categoria **Raccolta** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **ClearCollection\<T\>** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.ClearCollection%601> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito ClearCollection\<Int32\>.Per impostazione predefinita, *TypeArgument* è **Int32**.Tale valore può essere modificato nella griglia delle proprietà. È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **ClearCollection\<T\>** o nella casella **DisplayName** della griglia delle proprietà.Le altre proprietà devono essere modificate nella griglia delle proprietà.  
  
### Proprietà di ClearCollection\<T\>  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.ClearCollection%601> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Consente di specificare il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ClearCollection%601>.Il valore predefinito è ClearCollection\<Int32\>.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Specifica la raccolta di cui cancellare tutti gli elementi.Questa raccolta è di tipo **ICollection\<TypeArgument\>.** Per specificarla, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
|*TypeArgument*|True|Specifica il tipo T degli elementi contenuti in <xref:System.Collections.Generic.ICollection%601>.Per impostazione predefinita, questo tipo *TypeArgument* è impostato su **Int32**.Per cambiare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|  
  
## Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)