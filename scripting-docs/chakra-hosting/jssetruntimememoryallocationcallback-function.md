---
title: "Funzione JsSetRuntimeMemoryAllocationCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryAllocationCallback"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryAllocationCallback (funzione)"
ms.assetid: 6aa7d58d-6456-4df1-815f-1ba36fb4ae14
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsSetRuntimeMemoryAllocationCallback
Imposta un callback di allocazione di memoria per il runtime specificato  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryAllocationCallback(  
   _In_ JsRuntimeHandle runtime,  
   _In_opt_ void *callbackState,  
   _In_ JsMemoryAllocationCallback allocationCallback  
);  
```  
  
#### Parametri  
 `runtime`  
 Runtime per il quale registrare il callback di allocazione.  
  
 `callbackState`  
 Stato fornito dall'utente che verrà passato al callback.  
  
 `allocationCallback`  
 Callback di allocazione di memoria da chiamare per gli eventi di allocazione di memoria.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Registrare un callback di allocazione di memoria provocherà l'effetto di richiamare il runtime all'host ogni volta che questo acquisisce memoria dal, o libera memoria al, sistema operativo.  La routine di callback viene chiamata prima che il gestore di memoria del runtime allochi un blocco di memoria.  L'allocazione verrà rifiutata se il callback restituisce false.  Il gestore di memoria del runtime invocherà inoltre la routine di callback dopo aver liberato un blocco di memoria, così come dopo errori di allocazione.  
  
 Il callback viene richiamato sul thread in esecuzione nel runtime corrente, quindi l'esecuzione viene bloccata fino al completamento della chiamata.  
  
 Il valore restituito del callback non viene memorizzato; le allocazioni precedentemente rifiutate non impediscono al runtime di chiamare il callback in un secondo momento per le nuove allocazioni di memoria.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)