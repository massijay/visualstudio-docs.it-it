---
title: "Funzione JsGetTypedArrayStorage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 52e4ac5f-cc71-456d-95de-a48f7327503d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsGetTypedArrayStorage
Ottiene l'archivio di memoria sottostante usato da una matrice tipizzata.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayStorage(  
   _In_ JsValueRef typedArray,  
   _Outptr_result_bytebuffer_(*bufferLength) BYTE **buffer,  
   _Out_ unsigned int *bufferLength,  
   _Out_opt_ JsTypedArrayType *arrayType,  
   _Out_opt_ int *elementSize  
);  
```  
  
#### Parametri  
 `typedArray`  
 Istanza di matrice tipizzata.  
  
 `buffer`  
 Buffer della matrice.  Il ciclo di vita del buffer restituito è uguale alla durata della matrice.  Ai fini della procedura di Garbage Collection, il puntatore al buffer non viene considerato come riferimento alla matrice.  
  
 `bufferLength`  
 Numero di byte nel buffer.  
  
 `arrayType`  
 Tipo della matrice  
  
 `elementSize`  
 Dimensioni di un elemento della matrice.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)