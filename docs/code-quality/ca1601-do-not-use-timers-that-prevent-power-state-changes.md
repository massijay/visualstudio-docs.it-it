---
title: "CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza | Microsoft Docs"
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
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Category|Microsoft.Mobility|  
|Breaking Change|Breaking|  
  
## Causa  
 Sul timer è impostato un intervallo che ricorre più di una volta al secondo.  
  
## Descrizione della regola  
 Non utilizzare timer con un intervallo di polling o generazione superiore a una volta al secondo.  Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia che disattiva lo schermo e i dischi rigidi.  
  
## Come correggere le violazioni  
 Impostare gli intervalli del timer in modo che si verifichino con una frequenza inferiore a una volta al secondo.  
  
## Esclusione di avvisi  
 La regola dovrebbe essere esclusa solo se è richiesta l'attivazione del timer con intervalli superiori a una volta al secondo e le considerazioni sulla mobilità possono essere ignorate senza rischi.