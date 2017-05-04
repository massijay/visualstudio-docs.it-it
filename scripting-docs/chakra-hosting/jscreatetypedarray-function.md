---
title: "Funzione JsCreateTypedArray | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 937a2a91-6f5f-4aaa-a018-d3089702bf36
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsCreateTypedArray
Crea un oggetto matrice tipizzata JavaScript.  
  
## Sintassi  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateTypedArray(  
   _In_ JsTypedArrayType arrayType,  
   _In_ JsValueRef baseArray,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int elementLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Parametri  
 `arrayType`  
 Tipo della matrice da creare.  
  
 `baseArray`  
 Matrice di base della nuova matrice.  Usare `JS_INVALID_REFERENCE` se non esiste alcuna matrice di base.  
  
 `byteOffset`  
 Offset in byte a partire dall'inizio di `baseArray` \(`ArrayBuffer`\) a cui deve fare riferimento la matrice tipizzata del risultato.  Applicabile solo se `baseArray` è un oggetto `ArrayBuffer`;  in caso contrario, deve essere 0.  
  
 `elementLength`  
 Numero di elementi nella matrice.  Applicabile solo quando si crea una nuova matrice tipizzata senza `baseArray` \(`baseArray` è `JS_INVALID_REFERENCE`\) o quando `baseArray` è un oggetto `ArrayBuffer`;  in caso contrario, deve essere 0.  
  
 `result`  
 Nuovo oggetto matrice tipizzata.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 `baseArray` può essere un elemento `ArrayBuffer`, un'altra matrice tipizzata o un elemento `Array` JavaScript.  La matrice tipizzata restituita userà `baseArray` se è un elemento `ArrayBuffer`; in caso contrario, creerà e userà una copia della matrice di origine sottostante.  
  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)