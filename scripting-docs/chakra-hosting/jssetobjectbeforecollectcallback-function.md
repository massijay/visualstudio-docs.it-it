---
title: "Funzione JsSetObjectBeforeCollectCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione JsSetObjectBeforeCollectCallback
Imposta una funzione di callback che viene chiamata dal runtime prima dell'operazione di Garbage Collection di un oggetto.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### Parametri  
 `ref`  
 Oggetto per il quale registrare il callback.  
  
 `callbackState`  
 Stato fornito dall'utente passato al callback.  
  
 `objectBeforeCollectCallback`  
 Funzione di callback impostata.  Usare null per cancellare il callback registrato in precedenza.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
 Il callback viene richiamato sul thread in esecuzione nel runtime corrente, quindi l'esecuzione viene bloccata fino al completamento del callback.  
  
 Questa API è supportata solo in modalità Edge.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)