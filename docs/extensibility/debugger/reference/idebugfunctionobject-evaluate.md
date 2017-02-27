---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "Metodo IDebugFunctionObject::Evaluate"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

chiama la funzione e restituisce il valore risultante come oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### Parametri  
 `ppParams`  
 \[in\]  Una matrice [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) di oggetti che rappresentano i parametri di input.  Ognuno di questi parametri è stato creato con uno dei metodi di `Create` [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) nell'interfaccia.  
  
 `dwParams`  
 \[in\]  Il numero di parametri nella matrice di `ppParams` .  
  
 `dwTimeout`  
 \[in\]  Specifica il tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzo `INFINITE` attendere infinito.  
  
 `ppResult`  
 \[out\]  Restituisce [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) una rappresentazione del valore di funzione come un oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo è installato ed esegue una chiamata alla funzione rappresentata [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) dall'oggetto.  
  
## Vedere anche  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)