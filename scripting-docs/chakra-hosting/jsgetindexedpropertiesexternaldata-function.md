---
title: "Funzione JsGetIndexedPropertiesExternalData | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2c313163-3462-42fd-8dee-3dfb3ac7f43f
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsGetIndexedPropertiesExternalData
Recupera le informazioni relative ai dati esterni delle proprietà indicizzate di un oggetto.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetIndexedPropertiesExternalData(  
   _In_ JsValueRef object,  
   _Out_ void** data,  
   _Out_ JsTypedArrayType* arrayType,  
   _Out_ unsigned int* elementLength  
);  
```  
  
#### Parametri  
 `object`  
 Oggetto.  
  
 `data`  
 Archivio di backup dei dati esterni per le proprietà indicizzate dell'oggetto.  
  
 `arrayType`  
 Tipo di elemento di matrice nei dati esterni.  
  
 `elementLength`  
 Numero di elementi di matrice nei dati esterni.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)