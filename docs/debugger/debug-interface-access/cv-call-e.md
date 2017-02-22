---
title: "CV_call_e | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_call_e (enumerazione)"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica la convenzione di chiamata di una funzione.  
  
> [!NOTE]
>  Solo i valori di enumerazione più comuni sono illustrati di seguito.  Il censimento generale è disponibile nel file di intestazione di cvconst.h.  
  
## Sintassi  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elementi  
 CV\_CALL\_NEAR\_C  
 Specifica una convenzione di chiamata utilizzando una inserita da destra a sinistra vicina.  la funzione chiamante rimuove lo stack.  
  
 CV\_CALL\_NEAR\_FAST  
 Specifica una convenzione di chiamata utilizzando una inserita da sinistra a destra vicina con i registri.  La funzione chiamata utilizza la somma dei byte di parametro per rimuovere lo stack.  
  
 CV\_CALL\_NEAR\_STD  
 Specifica una convenzione di chiamata tramite una chiamata standard di chiusura \(inserita da destra a sinistra\).  
  
 CV\_CALL\_NEAR\_SYS  
 Specifica una convenzione di chiamata tramite una chiamata al sistema di chiusura.  
  
 CV\_CALL\_THISCALL  
 Specifica una convenzione di chiamata tramite `this` chiamata \(`this` puntatore passato nel log\).  
  
 CV\_CALL\_CLRCALL  
 Specifica una convenzione di chiamata utilizzata da Common Language Runtime \(CLR\) \(anche noto come una convenzione di chiamata di codice gestito\).  
  
## Note  
 I valori in questa enumerazione restituiti da una chiamata a [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) metodo.  
  
## Requisiti  
 intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)