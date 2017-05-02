---
title: "Funzione JsCreateDataView | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 161e59eb-d429-46f7-9a38-bbf2149ccf44
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsCreateDataView
Crea un oggetto `DataView` Javascript.  
  
## Sintassi  
  
```  
JsErrorCode  JsCreateDataView(  
   _In_ JsValueRef arrayBuffer,  
   _In_ unsigned int byteOffset,  
   _In_ unsigned int byteLength,  
   _Out_ JsValueRef *result  
);  
```  
  
#### Parametri  
 `arrayBuffer`  
 Oggetto `ArrayBuffer` esistente da usare come archivio per l'oggetto `DataView` del risultato.  
  
 `byteOffset`  
 Offset in byte a partire dall'inizio di `arrayBuffer` a cui deve fare riferimento l'elemento `DataView` del risultato.  
  
 `byteLength`  
 Numero di byte in ArrayBuffer a cui deve fare riferimento l'elemento DataView del risultato.  
  
 `result`  
 Nuovo oggetto DataView.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)