---
title: "Struttura DebugStackFrameDescriptor | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Struttura DebugStackFrameDescriptor"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Struttura DebugStackFrameDescriptor
Enumera gli stack frame e le unioni restituite da diversi enumeratori sullo stesso thread.  
  
## Sintassi  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## Membri  
 `pdsf`  
 L'oggetto dello stack frame.  
  
 `dwMin`  
 Una rappresentazione i dipendenti dell'intervallo minore degli indirizzi virtuali associata a questo stack frame.  
  
 `dwLim`  
 Una rappresentazione i dipendenti dell'intervallo maggiore degli indirizzi virtuali associata a questo stack frame.  
  
 `fFinal`  
 Diminuisca che indica che il frame sta sviluppando.  
  
 `punkFinal`  
 Se questo parametro non è `NULL`, l'unione corrente dell'enumeratore verrà arrestata e un nuovo deve essere avviato.  L'oggetto indica come avviare la nuova enumerazione.  
  
## Note  
 L'amministratore processo di debug utilizza questa struttura per ordinare gli stack frame dai moduli di gestione di script in.  Per convenzione, gli stack aumentano verso il basso.  Pertanto, nelle architetture degli stack crescono, indirizzi twos\- devono essere complementati.  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)