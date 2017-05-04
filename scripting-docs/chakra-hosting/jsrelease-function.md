---
title: "Funzione JsRelease | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRelease"
helpviewer_keywords: 
  - "JsRelease (funzione)"
ms.assetid: 8714fd0b-5b66-48e0-927e-7b93af6cde7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsRelease
Rilascia un riferimento a un oggetto raccolto dal Garbage Collector.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsRelease(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### Parametri  
 `ref`  
 Oggetto a cui aggiungere un riferimento.  
  
 `count`  
 Il nuovo conteggio dei riferimenti dell'oggetto \(può passare il valore null\).  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Rimuove un riferimento a un handle `JsRef` che è stato creato da `JsAddRef`.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)