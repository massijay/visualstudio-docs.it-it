---
title: "Personalizzazione dei controlli runtime nativi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
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
  - "/RTC (opzione del compilatore) [C++], controlli runtime nativo"
  - "personalizzazione del controllo di errori CRT"
  - "debugger, controlli runtime nativo"
  - "controlli runtime nativo, personalizzazione"
  - "runtime_checks (pragma)"
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Personalizzazione dei controlli runtime nativi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si compila l'applicazione con l'opzione per i controlli runtime **\/RTC** oppure si utilizza il pragma `runtime_checks`, nella libreria di runtime del linguaggio C sono disponibili controlli runtime nativi.  In alcuni casi può essere necessario personalizzare il controllo runtime:  
  
-   Per indirizzare i messaggi del controllo runtime a un file o una destinazione diversa da quella predefinita.  
  
-   Per specificare una destinazione di output dei messaggi del controllo runtime in un debugger di altri produttori.  
  
-   Per segnalare i messaggi del controllo runtime provenienti da un programma compilato con una versione di rilascio della libreria di runtime del linguaggio C.  Nelle versioni di rilascio della libreria per segnalare gli errori di runtime non viene utilizzato `_CrtDbgReportW` e viene invece visualizzata una finestra di dialogo di asserzione per ciascun errore di runtime.  
  
 Per personalizzare il controllo degli errori di runtime, è possibile utilizzare uno degli accorgimenti seguenti:  
  
-   Scrivere una funzione per la segnalazione degli errori di runtime.  Per ulteriori informazioni, vedere [Procedura: scrivere una funzione per la segnalazione degli errori di runtime](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   Personalizzare la destinazione dei messaggi di errore.  
  
-   Eseguire una query per ottenere informazioni sugli errori rilevati dai controlli runtime.  
  
## Personalizzare la destinazione dei messaggi di errore  
 Se si utilizza `_CrtDbgReportW` per la segnalazione degli errori, è possibile utilizzare `_CrtSetReportMode` per specificare la destinazione dei messaggi di errore.  
  
 Se si utilizza una funzione di segnalazione degli errori personalizzata, utilizzare `_RTC_SetErrorType` per associare un tipo di report a ciascun errore.  
  
## Eseguire una query per ottenere informazioni sui controlli runtime  
 `_RTC_NumErrors` restituisce il numero di tipi di errore rilevati dai controlli degli errori di runtime.  Per ottenere una breve descrizione di ciascun errore, è possibile creare un ciclo da 0 al valore restituito da `_RTC_NumErrors` passando il valore di iterazione a `_RTC_GetErrDesc` in ciascun ciclo.  Per ulteriori informazioni, vedere [\_RTC\_NumErrors](/visual-cpp/c-runtime-library/reference/rtc-numerrors) e [\_RTC\_GetErrDesc](/visual-cpp/c-runtime-library/reference/rtc-geterrdesc).  
  
## Vedere anche  
 [Procedura: utilizzare controlli runtime nativi](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime\_checks](/visual-cpp/preprocessor/runtime-checks)   
 [\_CrtDbgReport, \_CrtDbgReportW](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)