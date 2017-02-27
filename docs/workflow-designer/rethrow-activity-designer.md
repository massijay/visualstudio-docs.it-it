---
title: "ActivityDesigner Rethrow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Rethrow.UI"
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityDesigner Rethrow
L'ActivityDesigner **Rethrow** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Rethrow>.  
  
## Attività Rethrow  
 L'attività <xref:System.Activities.Statements.Rethrow> genera un'eccezione generata precedentemente.Questa attività può essere utilizzata solo in un gestore <xref:System.Activities.Statements.Catch> nell'attività <xref:System.Activities.Statements.TryCatch>.  
  
### Utilizzo dell'ActivityDesigner ReThrow  
 L'ActivityDesigner **ReThrow** è disponibile nella categoria **Gestione errori** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** a sinistra di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Rethrow** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.Rethrow> con la proprietà **DisplayName** impostata sul valore predefinito Throw.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Rethrow** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di Rethrow  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Rethrow> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Consente di specificare il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.ReThrow>.Il valore predefinito è Rethrow.|  
  
## Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)