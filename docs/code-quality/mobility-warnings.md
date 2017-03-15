---
title: "Avvisi di mobilit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "avvisi dell'analisi codice gestito, mobilità"
  - "avvisi di mobilità"
  - "avvisi, mobilità"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# Avvisi di mobilit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di mobilità supportano un utilizzo efficiente del consumo energetico.  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1600: Non impostare la priorità del processo su Inattivo](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Non impostare la priorità del processo su Inattivo.  I processi con System.Diagnostics.ProcessPriorityClass.Idle occupano la CPU, che diversamente sarebbe inattiva, e bloccano quindi la modalità standby.|  
|[CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia che disattiva lo schermo e i dischi rigidi.|