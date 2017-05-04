---
title: "Funzione JsIdle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIdle"
helpviewer_keywords: 
  - "JsIdle (funzione)"
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Funzione JsIdle
Indica al runtime di eseguire eventuali elaborazioni durante l'inattività che devono essere svolte.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### Parametri  
 `nextIdleTick`  
 Ciclo di sistema successivo in cui sarà presente ulteriore lavoro da svolgere durante l'inattività.  Può essere null.  Restituisce il numero massimo di cicli se non c'è lavoro imminente da svolgere durante l'inattività.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Se l'elaborazione durante l'inattività è stata abilitata per il runtime corrente, la chiamata di `JsIdle` informa il runtime corrente che l'host è inattivo e che il runtime può eseguire attività di pulizia della memoria.  
  
 `JsIdle` può anche restituire il numero di cicli di sistema fino a quando non sarà presente ulteriore lavoro che deve essere svolto dal runtime durante l'inattività.  Se si chiama `JsIdle` prima che sia passato questo numero di cicli, l'operazione non funziona.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)