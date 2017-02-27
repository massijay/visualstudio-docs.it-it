---
title: "ActivityDesigner Throw | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# ActivityDesigner Throw
L'ActivityDesigner **Throw** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Throw>.  
  
## Attività Throw  
 L'attività <xref:System.Activities.Statements.Throw> genera un'eccezione.  
  
### Utilizzo dell'ActivityDesigner Throw  
 L'ActivityDesigner **Throw** è disponibile nella categoria **Gestione errori** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** a sinistra di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Throw** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.Throw> con la proprietà **DisplayName** impostata sul valore predefinito Throw.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Throw** o nella casella **DisplayName** della griglia delle proprietà.La proprietà <xref:System.Activities.Statements.Throw.Exception%2A> deve essere modificata nella griglia delle proprietà.  
  
### Proprietà di Throw  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Throw> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.Throw>.Il valore predefinito è Throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|Eccezione da generare.Questa eccezione deve derivare da <xref:System.Exception>.Per specificare l'eccezione, digitare un'espressione Visual Basic nella griglia delle proprietà.|  
  
## Vedere anche  
 [Raccolta](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)