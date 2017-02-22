---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un oggetto che utilizza un costruttore immesso le impostazioni del flag di valutazione e un valore di timeout.  
  
## Sintassi  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### Parametri  
 `pConstructor`  
 \[in\]  [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Un oggetto che rappresenta il costruttore dell'oggetto da creare.  
  
 `dwArgs`  
 \[in\]  Il numero di parametri nella matrice di `pArg` .  Rappresenta il numero dei parametri passati al costruttore.  
  
 `pArgs`  
 \[in\]  Una matrice [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) di oggetti che rappresenta i parametri passati al costruttore.  
  
 `dwEvalFlags`  
 \[in\]  Una combinazione di flag [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) dall'enumerazione che specificano come la valutazione è necessario eseguire.  
  
 `dwTimeout`  
 \[in\]  Tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzare **INFINITY** attendere infinito.  
  
 `ppObject`  
 \[out\]  Restituisce **un IDebugObject** che rappresenta l'oggetto appena creato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Chiamare questo metodo per creare un oggetto che rappresenta un'istanza di una classe, o un altro tipo complesso che richiede un costruttore, un parametro.  
  
## Vedere anche  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)