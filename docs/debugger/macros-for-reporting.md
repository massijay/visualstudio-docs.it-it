---
title: "Macro per la creazione di rapporti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_RPTFn (macro)"
  - "_RPTn (macro)"
  - "CRT, macro per la creazione di rapporti"
  - "debug [CRT], macro per la creazione di rapporti"
  - "macro, macro per la creazione di rapporti CRT"
  - "macro, debug"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Macro per la creazione di rapporti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare le macro **\_RPTn** e **\_RPTFn**, definite in CRTDBG.H, per sostituire l'utilizzo di istruzioni `printf` per il debug.  Queste macro vengono automaticamente eliminate nella build di rilascio quando non è definito **\_DEBUG**, pertanto non è necessario racchiuderle tra istruzioni **\#ifdef**.  
  
|Macro|Descrizione|  
|-----------|-----------------|  
|**\_RPT0**, **\_RPT1**, **\_RPT2**, **\_RPT3**, **\_RPT4**|Genera una stringa di messaggio e da zero a quattro argomenti.  Da \_RPT1 a **\_RPT4** la stringa di messaggio funge da stringa di formattazione di tipo printf per gli argomenti.|  
|**\_RPTF0**, **\_RPTF1**, **, \_RPTF2**, **\_RPTF4**|Come **\_RPTn**, ma queste macro generano anche il nome file e il numero di riga in cui si trova la macro.|  
  
 Si consideri l'esempio seguente:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Questo codice invia a **stdout** i valori di `someVar` e `otherVar`.  È possibile utilizzare la chiamata di `_RPTF2` che segue per restituire questi stessi valori nonché il nome file e il numero di riga:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Se si ritiene che una particolare applicazione necessiti di un tipo di report di debug che le macro fornite con la libreria di runtime del linguaggio C non offrono, sarà possibile scrivere una macro progettata appositamente per rispondere alle esigenze specifiche.  In uno dei file di intestazione, ad esempio, è possibile includere un codice simile al seguente per definire una macro denominata **ALERT\_IF2**:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 Una chiamata a **ALERT\_IF2** consente di eseguire tutte le funzioni del codice **printf** illustrato all'inizio di questo argomento:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Dal momento che è possibile modificare facilmente una macro personalizzata in modo che invii un report con più o meno informazioni a diverse destinazioni \(a seconda di ciò che risulta più comodo\), questa tecnica può rivelarsi particolarmente utile con l'evolversi delle esigenze di debug.  
  
## Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)