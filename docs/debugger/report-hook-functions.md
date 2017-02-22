---
title: "Funzioni hook per la creazione di rapporti | Microsoft Docs"
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
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtDbgReport (funzione)"
  - "_CrtSetReportHook (funzione)"
  - "debugger, funzioni hook per la creazione di rapporti"
  - "debug [C++], funzioni hook"
  - "hook, rapporto"
  - "allocazione di memoria, heap di debug"
  - "funzioni hook per la creazione di rapporti"
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funzioni hook per la creazione di rapporti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una funzione hook per la creazione di report, installata mediante [\_CrtSetReportHook](/visual-cpp/c-runtime-library/reference/crtsetreporthook), viene chiamata ogni volta che [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) genera un report di debug.  È possibile utilizzare tale funzione, ad esempio, per filtrare i report in modo da concentrarsi su tipi specifici di allocazioni.  Una funzione hook per la creazione di report deve avere un prototipo analogo al seguente:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 Il puntatore che viene passato a **\_CrtSetReportHook** è del tipo **\_CRT\_REPORT\_HOOK**, come definito in CRTDBG.H:  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Quando la libreria di runtime chiama la funzione hook, l'argomento *nRptType* contiene la categoria del report \(**\_CRT\_WARN**, **\_CRT\_ERROR** o **\_CRT\_ASSERT**\), *szMsg* contiene un puntatore a una stringa di messaggio di report completa e *retVal* specifica se `_CrtDbgReport` debba continuare la normale esecuzione dopo la generazione del report o avviare invece il debugger \(se *retVal* ha valore zero l'esecuzione continua, se ha valore 1 viene avviato il debugger\).  
  
 Se la funzione hook gestisce il messaggio in questione completamente, in modo che non sia necessario alcun report ulteriore, deve restituire **TRUE**.  Se restituisce **FALSE**, `_CrtDbgReport` visualizzerà il messaggio normalmente.  
  
## Vedere anche  
 [Scrittura di funzioni hook di debug](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/it-it/21e1346a-6a17-4f57-b275-c76813089167)