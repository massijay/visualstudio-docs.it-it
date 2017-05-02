---
title: "Funzione JsAddRef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef (funzione)"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsAddRef
Aggiunge un riferimento a un oggetto raccolto dal Garbage Collector.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
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
 Questa operazione deve essere chiamata solo sul gestore `JsRef` che non sarà archiviato in un punto nello stack.  Chiamando `JsAddRef` si garantisce che l'oggetto a cui `JsRef` si riferisce non sarà liberato finché non verrà chiamato `JsRelease`.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)