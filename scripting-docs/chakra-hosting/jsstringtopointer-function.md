---
title: "Funzione JsStringToPointer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStringToPointer"
helpviewer_keywords: 
  - "JsStringToPointer (funzione)"
ms.assetid: c7aa7a09-489d-4435-8f8a-aeb62f8875ae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsStringToPointer
Recupera il puntatore di stringa di un valore di stringa.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsStringToPointer(  
   _In_ JsValueRef value,  
   _Outptr_result_buffer_(*stringLength) const wchar_t **stringValue,  
   _Out_ size_t *stringLength  
);  
```  
  
#### Parametri  
 `value`  
 Valore di stringa da convertire in un puntatore di stringa.  
  
 `stringValue`  
 Puntatore di stringa.  
  
 `stringLength`  
 Lunghezza della stringa.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Questa funzione recupera il puntatore di stringa di un valore di stringa.  Non riesce con `JsErrorInvalidArgument` se il valore non è di tipo stringa.  La durata della stringa restituita sarà uguale a quella del valore da cui proviene. Tuttavia, il puntatore di stringa non viene considerato un riferimento al valore \(quindi verrà escluso dalla raccolta\).  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)