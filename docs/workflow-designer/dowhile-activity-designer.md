---
title: "ActivityDesigner DoWhile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.DoWhile.UI"
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ActivityDesigner DoWhile
L'attività <xref:System.Activities.Statements.DoWhile> esegue almeno una volta l'attività contenuta nel rispettivo <xref:System.Activities.Statements.DoWhile.Body%2A> fino a che una condizione specificata restituisce **false**.Se è necessario non eseguire l'attività contenuta in un corpo del ciclo o eseguirla più volte, utilizzare l'attività alternativa <xref:System.Activities.Statements.While>.  
  
## Proprietà di DoWhile in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.DoWhile> e ne viene descritto l'utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|L'attività da eseguire se la condizione è **true**.Per aggiungere l'attività <xref:System.Activities.Statements.DoWhile.Body%2A>, trascinare un'attività dalla casella degli strumenti e rilasciarla nella casella **Body** dell'ActivityDesigner **DoWhile** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Condizione da valutare prima di ogni iterazione del ciclo.Per impostare la proprietà <xref:System.Activities.Statements.DoWhile.Condition%2A>, digitare un'espressione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nella casella **Condition** nell'ActivityDesigner **DoWhile** oppure nella griglia delle proprietà.|  
  
## Vedere anche  
 [While](../workflow-designer/while-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)