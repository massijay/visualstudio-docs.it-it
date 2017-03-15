---
title: "Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.runtime"
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
  - "CRT, controlli runtime"
  - "debugger, controlli runtime nativo"
  - "debug [Visual Studio], routine di runtime"
  - "controlli runtime, /RTC (opzione)"
  - "errori di runtime, controlli di errori"
  - "errori di runtime, controlli runtime"
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Utilizzo dei controlli runtime senza la libreria di runtime del linguaggio C
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se il programma viene collegato senza la libreria di runtime del linguaggio C tramite l'opzione **\/NODEFAULTLIB** e si desidera utilizzare i controlli runtime, è necessario stabilire il collegamento con la libreria RunTmChk.lib.  
  
 `_RTC_Initialize` consente di inizializzare il programma per i controlli runtime.  Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario verificare che il programma sia compilato con i controlli degli errori di runtime prima di chiamare `_RTC_Initialize`, come illustrato di seguito:  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 Se non si stabilisce il collegamento con la libreria di runtime del linguaggio C, è necessario definire anche una funzione chiamata `_CRT_RTC_INITW`.  `_CRT_RTC_INITW` consente di installare la funzione definita dall'utente come funzione di segnalazione degli errori predefinita, come illustrato di seguito:  
  
```  
// C version:  
_RTC_error_fnW __cdecl _CRT_RTC_INITW(  
        void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler.  
    return &MyErrorFunc;   
}  
  
// C++ version:  
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(  
       void *res0, void **res1, int res2, int res3, int res4)  
{  
    // set the error handler:  
    return &MyErrorFunc;  
}  
```  
  
 Dopo aver installato la funzione di segnalazione degli errori predefinita, sarà possibile installare altre funzioni di segnalazione degli errori con `_RTC_SetErrorFuncW`.  Per ulteriori informazioni, vedere [\_RTC\_SetErrorFuncW](/visual-cpp/c-runtime-library/reference/rtc-seterrorfuncw).  
  
## Vedere anche  
 [Procedura: utilizzare controlli runtime nativi](../debugger/how-to-use-native-run-time-checks.md)