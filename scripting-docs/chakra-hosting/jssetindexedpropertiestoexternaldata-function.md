---
title: "Funzione JsSetIndexedPropertiesToExternalData | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cee2d86d-ed42-4acb-86ef-95a67e63d0d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsSetIndexedPropertiesToExternalData
Imposta le proprietà indicizzate di un oggetto ai dati esterni.  I dati esterni verranno usati come archivio di backup per le proprietà indicizzate dell'oggetto, a cui accedere come matrice tipizzata.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetIndexedPropertiesToExternalData(  
   _In_ JsValueRef object,  
   _In_ void* data,  
   _In_ JsTypedArrayType arrayType,  
   _In_ unsigned int elementLength  
);  
```  
  
#### Parametri  
 `object`  
 Oggetto su cui eseguire l'operazione.  
  
 `data`  
 Dati esterni da usare come archivio di backup per le proprietà indicizzate dell'oggetto.  
  
 `arrayType`  
 Tipo di elemento di matrice nei dati esterni.  
  
 `elementLength`  
 Numero di elementi di matrice nei dati esterni.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)