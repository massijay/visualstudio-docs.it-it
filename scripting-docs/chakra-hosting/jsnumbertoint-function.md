---
title: "Funzione JsNumberToInt | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Funzione JsNumberToInt
Recupera il valore `int` di un valore numerico.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### Parametri  
 `value`  
 Valore numerico da convertire in un valore `int`.  
  
 `intValue`  
 Valore `int`.  
  
## Valore restituito  
  
## Note  
 Questa funzione recupera il valore di un valore numerico e lo converte in un valore `int`.  Avrà esito negativo con `JsErrorInvalidArgument` se il tipo del valore non è numerico.  
  
 Richiede un contesto di script attivo.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)