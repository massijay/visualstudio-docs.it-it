---
title: "ActivityDesigner ForEach&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityDesigner ForEach&lt;T&gt;
L'attività <xref:System.Activities.Statements.ForEach%601> esegue l'attività contenuta nel rispettivo oggetto <xref:System.Activities.Statements.ForEach%601.Body%2A> per ogni elemento di una raccolta di  <xref:System.Activities.Statements.ForEach%601.Values%2A> specificata.  
  
## Proprietà di ForEach\<T\> in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ForEach%601> e ne viene descritto l'utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Necessaria|Utilizzo|  
|--------------------|----------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ForEach%601>.Il valore predefinito è ForEach\<Int32\>.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Raccolta di elementi da scorrere.Per impostare la proprietà <xref:System.Activities.Statements.ForEach%601.Values%2A>, digitare un'espressione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nella casella **Values** nell'ActivityDesigner **ForEach\<T\>** o nella griglia delle proprietà.|  
|*TypeArgument*|True|Tipo degli elementi della raccolta <xref:System.Activities.Statements.ForEach%601.Values%2A> specificato dal parametro generico *T*.Per impostazione predefinita, la proprietà *TypeArgument* è impostata su **Int32**.Per cambiare il tipo, modificare il valore di *TypeArgument* nella casella combinata della griglia delle proprietà.|  
  
 Per impostazione predefinita, l'iteratore del ciclo è denominato **item**.È possibile modificare il nome della variabile di iteratore nell'ActivityDesigner <xref:System.Activities.Statements.ForEach%601>.L'iteratore del ciclo può essere utilizzato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ForEach%601>.  
  
## Vedere anche  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)