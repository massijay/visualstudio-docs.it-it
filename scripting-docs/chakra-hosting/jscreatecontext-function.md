---
title: "Funzione JsCreateContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext (funzione)"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Funzione JsCreateContext
Crea un contesto di script per l'esecuzione di script.  
  
## Sintassi  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### Parametri  
 `runtime`  
 Runtime in cui viene creato il contesto di script.  
  
 `debugApplication`  
 Applicazione di debug da usare per il debug.  Questo parametro può essere null. In questo caso, il debug non è abilitato per il contesto.  
  
 `newContext`  
 Il contesto di script creato.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Ogni contesto di script ha un proprio oggetto globale isolato da tutti gli altri contesti di script.  
  
 Il parametro `debugApplication` non è supportato in modalità Bordo.  Per altre informazioni sull'uso dell'API in modalità Bordo, vedere [Scelta del motore Edge o del motore legacy](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)