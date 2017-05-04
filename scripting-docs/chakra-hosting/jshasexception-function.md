---
title: "Funzione JsHasException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException (funzione)"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsHasException
Determina se il runtime del contesto corrente è in uno stato di eccezione.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### Parametri  
 `hasException`  
 Se il runtime del contesto corrente è in stato di eccezione.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Se una chiamata al runtime genera un'eccezione \(in seguito all'esecuzione di uno script o a causa di un evento come un errore di conversione\), il runtime viene impostato su uno "stato di eccezione". Tutte le chiamate a un contesto creato dal runtime \(tranne le API di eccezione\) non riusciranno con `JsErrorInExceptionState` finché l'eccezione non viene eliminata.  
  
 Se il runtime del contesto corrente è in stato di eccezione quando un callback torna nel motore, il motore genera di nuovo l'eccezione automaticamente.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)