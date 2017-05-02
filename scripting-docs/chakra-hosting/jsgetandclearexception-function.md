---
title: "Funzione JsGetAndClearException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException (funzione)"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsGetAndClearException
Restituisce l'eccezione che ha causato lo stato d'eccezione del runtime del contesto corrente e reimposta lo stato di eccezione per quel runtime.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### Parametri  
 `exception`  
 Eccezione per il runtime del contesto corrente.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Se il runtime del contesto corrente non si trova in uno stato di eccezione, questa API restituirà `JsErrorInvalidArgument`.  Se il runtime è disabilitato, questo restituirà un'eccezione che indica che lo script è stato interrotto, ma non annullerà l'eccezione \(l'eccezione verrà annullata se il runtime viene riabilitato usando `JsEnableRuntimeExecution`\).  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)