---
title: "Funzione JsDisableRuntimeExecution | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution (funzione)"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsDisableRuntimeExecution
Sospende l'esecuzione di script e termina tutti gli script in esecuzione nel runtime.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### Parametri  
 `runtime`  
 Il runtime da sospendere.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Le chiamate a runtime sospesi non verranno eseguite correttamente finché `JsEnableRuntimeExecution` viene chiamata.  
  
 Questa API non deve essere chiamata su un thread che è attivo sul runtime.  Nonostante il runtime venga impostato in uno stato sospeso, uno script in esecuzione non può essere sospeso contemporaneamente; lo script in esecuzione verrà terminato con un'eccezione non catturabile il prima possibile.  
  
 Sospendere l'esecuzione in un runtime che è già stato sospeso è un'operazione che non produce effetti.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)