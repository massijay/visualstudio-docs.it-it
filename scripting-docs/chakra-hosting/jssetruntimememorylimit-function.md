---
title: "Funzione JsSetRuntimeMemoryLimit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetRuntimeMemoryLimit"
helpviewer_keywords: 
  - "JsSetRuntimeMemoryLimit (funzione)"
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsSetRuntimeMemoryLimit
Imposta il limite di memoria corrente per il runtime.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### Parametri  
 `runtime`  
 Il runtime il cui limite di memoria viene impostato.  
  
 `memoryLimit`  
 Il nuovo limite di memoria del runtime, in byte oppure \-1 per non limitare la memoria.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Un limite di memoria comporta che una qualsiasi operazione che supera il limite fallisce restituendo un errore "memoria insufficiente".  Impostare il limite di memoria del runtime a \-1 indica che il runtime non ha limite di memoria.  I nuovi runtime, come impostazione predefinita, non hanno limiti di memoria.  Se il nuovo limite di memoria supera l'utilizzo corrente, la chiamata avrà esito positivo e tutte le future allocazioni in questo runtime avranno esito negativo fino a che l'utilizzo della memoria del runtime non scenderà sotto il limite.  
  
 Il limite di memoria del runtime può essere sempre impostato, indipendentemente dal fatto che il runtime sia attivo in un altro thread.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)