---
title: "IDebugFunctionObject2::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::Evaluate"
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFunctionObject2::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

chiama la funzione e restituisce il valore risultante come oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### Parametri  
 `ppParams`  
 \[in\]  Una matrice [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) di oggetti che rappresenta i parametri di input.  Ognuno di questi parametri è stato creato utilizzando uno dei metodi di creazione in questa interfaccia.  
  
 `dwParams`  
 \[in\]  Il numero di parametri nella matrice di `ppParams` .  
  
 `dwEvalFlags`  
 \[in\]  Una combinazione di flag [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) dall'enumerazione che specificano come la valutazione è necessario eseguire.  
  
 `dwTimeout`  
 \[in\]  Specifica il tempo massimo, in millisecondi, di attendere prima di uscire da questo metodo.  Utilizzare **INFINITY** attendere infinito.  
  
 `ppResult`  
 \[out\]  Restituisce **un IDebugObject** che rappresenta il valore di funzione come un oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)