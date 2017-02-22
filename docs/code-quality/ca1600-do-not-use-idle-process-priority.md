---
title: "CA1600: Non impostare la priorit&#224; del processo su Inattivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1600: Non impostare la priorit&#224; del processo su Inattivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Category|Microsoft.Mobility|  
|Breaking Change|Breaking|  
  
## Causa  
 Questa regola si verifica quando i processi sono impostati su `ProcessPriorityClass.Idle`.  
  
## Descrizione della regola  
 Non impostare la priorità del processo su Inattivo.  I processi con `System.Diagnostics.ProcessPriorityClass.Idle` occupano la CPU che diversamente sarebbe inattiva e bloccano quindi la modalità standby.  
  
## Come correggere le violazioni  
 Impostare i processi su `ProcessPriorityClass.BelowNormal`.  
  
## Esclusione di avvisi  
 Questa regola dovrebbe essere esclusa solo se è necessaria una priorità di processo Inattivo ed è possibile ignorare le considerazioni di mobilità senza problemi di sicurezza.