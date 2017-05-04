---
title: "Funzione JsEnumerateHeap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnumerateHeap"
helpviewer_keywords: 
  - "JsEnumerateHeap (funzione)"
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsEnumerateHeap
Enumera l'heap del contesto corrente.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### Parametri  
 `enumerator`  
 Enumeratore dell'heap.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Durante l'enumerazione dell'heap, il contesto corrente non può essere rimosso e tutte le chiamate per modificare lo stato del contesto non riescono fino a quando l'enumeratore dell'heap non viene rilasciato.  
  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata nelle app desktop, ma non nelle app di Windows Store.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)