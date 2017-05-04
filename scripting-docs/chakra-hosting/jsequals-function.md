---
title: "Funzione JsEquals | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEquals"
helpviewer_keywords: 
  - "JsEquals (funzione)"
ms.assetid: 8377a7b6-12ff-43e4-8cc8-5a5a198a168b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsEquals
Confrontare due valori JavaScript per verificarne l'uguaglianza.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### Parametri  
 `object1`  
 Primo oggetto da confrontare.  
  
 `object2`  
 Secondo oggetto da confrontare.  
  
 `result`  
 Se i valori sono uguali.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Questa funzione è equivalente all'operatore `==` in Javascript.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)