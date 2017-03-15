---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "Enumerazione EVALFLAGS"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica i flag che controllano la valutazione di espressioni.  
  
## Sintassi  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```c#  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## Membri  
 EVAL\_RETURNVALUE  
 Specifica che il valore restituito, se presente, viene valutato.  
  
 EVAL\_NOSIDEEFFECTS  
 Specifica gli effetti collaterali per non perché.  
  
 EVAL\_ALLOWBPS  
 specifica arrestare sui punti di interruzione.  
  
 EVAL\_ALLOWERRORREPORT  
 Specifica la segnalazione errori all'host perché le sia.  Principalmente utilizzato per la valutazione di espressioni in script in Internet Explorer.  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 Impone l'esecuzione per essere valutata come indirizzi, anziché chiamare la funzione.  
  
 EVAL\_NOFUNCEVAL  
 Impedisce la funzione dalla valutazione.  Ad esempio, si consideri il token di `int` nell'espressione `myExpression(int) + 10`.  Questa funzione può essere correttamente valutata come indirizzo, ma non come valore.  
  
 EVAL\_NOEVENTS  
 Flag per indicare che gli eventi che si verificano durante la valutazione di espressioni non devono essere inviati al gestore di debug della sessione \(SDM\) o all'IDE.  
  
## Note  
 Questi flag vengono passati come argomento [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ai metodi e.  
  
 Questi flag possono essere combinati con un OR bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)