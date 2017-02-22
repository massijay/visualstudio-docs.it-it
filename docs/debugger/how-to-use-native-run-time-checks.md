---
title: "Procedura: utilizzare controlli runtime nativi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.errorchecks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/O (opzione del compilatore), /RTC (opzione)"
  - "/RTC (opzione del compilatore) [C++], /O (opzione del compilatore)"
  - "matrici [Visual Studio], debug"
  - "debugger, controlli runtime nativo"
  - "debugger, errori di runtime"
  - "debug di matrici"
  - "controlli runtime nativo"
  - "O (opzione del compilatore), /RTC (opzione)"
  - "opzione compilazione ottimizzata"
  - "RTC (opzione del compilatore), /O (opzione del compilatore)"
  - "controlli runtime"
  - "controlli runtime, nativi"
  - "errori di runtime, debug"
  - "errori di runtime, controlli di errori"
  - "runtime_checks (pragma)"
  - "puntatori di stack"
  - "puntatori di stack, danneggiamento"
  - "stack, danneggiamento del puntatore"
  - "variabili [debugger], intercettazione di dipendenze su variabili locali non inizializzate"
  - "variabili [debugger], perdita di dati"
ms.assetid: dc7b2f1e-5ff6-42e0-89b3-dc9dead83ee1
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare controlli runtime nativi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual C\+\+ è possibile usare [runtime\_checks](/visual-cpp/preprocessor/runtime-checks) nativi per rilevare errori di runtime comuni, ad esempio:  
  
-   Errori del puntatore dello stack.  
  
-   Sovraccarichi di matrici locali.  
  
-   Errori dello stack.  
  
-   Dipendenze da variabili locali non inizializzate.  
  
-   Perdita di dati a causa dell'assegnazione a una variabile di lunghezza inferiore.  
  
 Se si usa l'opzione **\/RTC** con una build ottimizzata \(**\/O**\), verrà restituito un errore del compilatore. Se si usa un pragma `runtime_checks` in una build ottimizzata, il pragma non avrà effetto.  
  
 Durante il debug di un programma in cui sono attivi i controlli runtime, l'azione predefinita quando si verifica un errore di runtime è l'arresto del programma e il passaggio al debugger. Tale comportamento predefinito può essere modificato per qualsiasi controllo runtime. Per altre informazioni, vedere [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Nelle procedure riportate di seguito viene descritto come attivare i controlli runtime nativi in una build di debug e come modificare il comportamento di tali controlli.  
  
 Negli altri argomenti di questa sezione vengono fornite informazioni relative a:  
  
-   [Personalizzazione dei controlli runtime nativi](../debugger/native-run-time-checks-customization.md)  
  
-   [Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)  
  
### Per attivare i controlli runtime nativi in una build di debug  
  
-   Usare l'opzione **\/RTC** e collegarsi alla versione di debug di una libreria di runtime del linguaggio C, ad esempio \/MDd.  
  
### Per modificare il comportamento dei controlli runtime nativi  
  
-   Usare il pragma `runtime_checks`.  
  
## Vedere anche  
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [Controllo degli errori di runtime](/visual-cpp/c-runtime-library/run-time-error-checking)