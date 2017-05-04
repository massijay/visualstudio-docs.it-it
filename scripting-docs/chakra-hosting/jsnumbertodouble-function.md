---
title: "Funzione JsNumberToDouble | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsNumberToDouble"
helpviewer_keywords: 
  - "JsNumberToDouble (funzione)"
ms.assetid: 5f52e8b6-2b70-49a3-879a-bd83ebf2ac33
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsNumberToDouble
Recupera il valore `double` di un valore numerico.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsNumberToDouble(  
   _In_ JsValueRef value,  
   _Out_ double *doubleValue  
);  
```  
  
#### Parametri  
 `value`  
 Valore numerico da convertire in un valore `double`.  
  
 `doubleValue`  
 Valore `double`.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Questa funzione recupera il valore di un valore numerico.  Avrà esito negativo con `JsErrorInvalidArgument` se il tipo del valore non è numerico.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)