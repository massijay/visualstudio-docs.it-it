---
title: "Codice misto e informazioni mancanti nella finestra Stack di chiamate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "codice gestito, esecuzione di istruzioni"
  - "Finestra Stack di chiamate, debug in modalità mista"
  - "Finestra Stack di chiamate, risoluzione dei problemi"
  - "frame nativi"
  - "stack di chiamate gestito"
  - "debug in modalità mista, stack di chiamate"
  - "uscita, codice gestito"
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Codice misto e informazioni mancanti nella finestra Stack di chiamate
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A causa delle differenze tra gli stack di chiamate per il codice gestito e il codice nativo, il debugger non è sempre in grado di visualizzare lo stack di chiamate completo in caso di tipi di codice misti.  Quando codice nativo chiama codice gestito, nella finestra **Stack di chiamate** potrebbero osservarsi le seguenti discrepanze:  
  
-   Il frame nativo situato immediatamente al di sopra del codice gestito potrebbe non essere visualizzato nella finestra **Stack di chiamate**.  Per ulteriori informazioni, vedere [Procedura: uscire da codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
-   Per le applicazioni in modalità mista avviate all'esterno del debugger, nella finestra **Stack di chiamate** potrebbe essere visualizzato solo il codice gestito ma nessuno dei frame nativi.  
  
 Entrambi i casi sono piuttosto rari.  Nella maggior parte delle chiamate native a codice gestito gli stack di chiamate verranno visualizzati in modo corretto.  
  
## Vedere anche  
 [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)