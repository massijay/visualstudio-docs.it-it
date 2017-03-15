---
title: "CA1809: Evitare un numero eccessivo di variabili locali | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1809: Evitare un numero eccessivo di variabili locali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro contiene più di 64 variabili locali, alcune delle quali potrebbero essere generate dal compilatore.  
  
## Descrizione della regola  
 Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria. Tale procedura è definita *registrazione* del valore.  Common Language Runtime considera per la registrazione fino a 64 variabili locali.  Le variabili non registrate sono posizionate sullo stack e devono essere spostate in un registro prima della modifica.  Per offrire una possibilità di registrazione a tutte le variabili locali, limitare il numero di tali variabili a 64.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, effettuare il refactoring dell'implementazione in modo che non utilizzi più di 64 variabili locali.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola così come la disabilitazione della regola, è sicura se le prestazioni non costituiscono un problema.  
  
## Regole correlate  
 [CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)