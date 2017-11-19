---
title: ForEach&lt;T&gt; ActivityDesigner | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecfdc4d736f2be4ba4a8810b039ac11c88228160
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; ActivityDesigner
L'attività <xref:System.Activities.Statements.ForEach%601> esegue l'attività contenuta nel rispettivo oggetto <xref:System.Activities.Statements.ForEach%601.Body%2A> per ogni elemento di una raccolta di <xref:System.Activities.Statements.ForEach%601.Values%2A> specificata.  
  
## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\> proprietà nella finestra di progettazione del flusso di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.ForEach%601> e ne viene descritto l'uso nella finestra di progettazione.  
  
|Nome proprietà|Obbligatorio|Utilizzo|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.ForEach%601>. Il valore predefinito è ForEach < Int32\>. Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|Raccolta di elementi da scorrere. Per impostare il <xref:System.Activities.Statements.ForEach%601.Values%2A>, digitare un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] espressione il **valori** casella il **ForEach < T\>**  attività della finestra di progettazione o nella griglia delle proprietà.|  
|*TypeArgument*|True|Il tipo degli elementi di <xref:System.Activities.Statements.ForEach%601.Values%2A> raccolta specificata dal parametro generico *T*. Per impostazione predefinita, *TypeArgument* è impostato su **Int32**. Per modificare il tipo, modificare il valore di *TypeArgument* casella combinata nella griglia delle proprietà.|  
  
 Per impostazione predefinita, l'iteratore del ciclo è denominato **elemento**. È possibile modificare il nome della variabile di iteratore nell'ActivityDesigner <xref:System.Activities.Statements.ForEach%601>. L'iteratore del ciclo può essere usato nelle espressioni contenute in elementi figlio dell'attività <xref:System.Activities.Statements.ForEach%601>.  
  
## <a name="see-also"></a>Vedere anche  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)