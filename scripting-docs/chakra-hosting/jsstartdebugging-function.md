---
title: "Funzione JsStartDebugging | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartDebugging"
helpviewer_keywords: 
  - "JsStartDebugging (funzione)"
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Funzione JsStartDebugging
Avvia il debug nel contesto corrente.  
  
## Sintassi  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### Parametri  
 `debugApplication`  
 Applicazione di debug da usare per il debug.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 L'host deve verificare che `CoInitializeEx` sia chiamato con `COINIT_MULTITHREADED` o `COINIT_APARTMENTTHREADED` almeno una volta prima di usare questa API  
  
 Il parametro `debugApplication` non è supportato in modalità Bordo.  Per altre informazioni sull'uso dell'API in modalità Bordo, vedere [Scelta del motore Edge o del motore legacy](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)