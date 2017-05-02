---
title: "Funzione JsGetArrayBufferStorage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 712ae298-36a9-47ef-b089-e51835c056bc
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsGetArrayBufferStorage
Ottiene l'archivio di memoria sottostante usato da un elemento `ArrayBuffer`.  
  
## Sintassi  
  
```  
JsErrorCode STDAPI_ JsGetArrayBufferStorage(  
   _In_ JsValueRef arrayBuffer,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength  
);  
```  
  
#### Parametri  
 `arrayBuffer`  
 Istanza di ArrayBuffer.  
  
 `buffer`  
 Buffer di ArrayBuffer.  Il ciclo di vita del buffer restituito è uguale alla durata dell'elemento `ArrayBuffer`.  Ai fini della procedura di Garbage Collection, il puntatore al buffer non viene considerato come riferimento all'elemento `ArrayBuffer`.  
  
 `bufferLength`  
 Numero di byte nel buffer.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)