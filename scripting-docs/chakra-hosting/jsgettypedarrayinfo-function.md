---
title: "Funzione JsGetTypedArrayInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992bc4e9-3d06-4ad2-8b6b-88a437360f81
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione JsGetTypedArrayInfo
Ottiene le proprietà più usate di una matrice tipizzata.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetTypedArrayInfo(  
  _In_ JsValueRef typedArray,  
  _Out_opt_ JsTypedArrayType *arrayType,  
  _Out_opt_ JsValueRef *arrayBuffer,  
  _Out_opt_ unsigned int *byteOffset,  
  _Out_opt_ unsigned int *byteLength  
);  
  
```  
  
#### Parametri  
 `typedArray`  
 Istanza di matrice tipizzata.  
  
 `arrayType`  
 Tipo della matrice  
  
 `arrayBuffer`  
 Backstore `ArrayBuffer` della matrice.  
  
 `byteOffset`  
 Offset in byte dall'inizio di un elemento arrayBuffer a cui viene fatto riferimento nella matrice.  
  
 `byteLength`  
 Numero di byte presenti nella matrice.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)