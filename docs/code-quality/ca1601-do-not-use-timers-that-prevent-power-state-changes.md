---
title: 'CA1601: Non utilizzare i timer che impediscono le modifiche dello stato di alimentazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5fc42c15beda68472f4a980fe96b0055b70a01cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Non utilizzare i timer che impediscono le modifiche allo stato di potenza
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Categoria|Microsoft.Mobility|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un timer è un intervallo impostato su cui si verificano più di una volta al secondo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Intervallo di polling di una volta al secondo o utilizzare i timer che si verificano più frequentemente una volta al secondo. Una frequenza maggiore per l'attività periodica occupa la CPU e interferisce con i timer di inattività per il risparmio di energia tramite cui vengono disattivati lo schermo e i dischi rigidi.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Impostare gli intervalli di timer in presenti meno di una volta al secondo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Questa regola deve essere eliminata solo se è richiesta l'attivazione di più di una volta al secondo il timer e le considerazioni di mobilità possono essere ignorate.