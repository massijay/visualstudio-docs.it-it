---
title: "Funzione JsIsRuntimeExecutionDisabled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIsRuntimeExecutionDisabled"
helpviewer_keywords: 
  - "JsIsRuntimeExecutionDisabled (funzione)"
ms.assetid: 77490280-fb84-4614-a1f0-6ac31e3bd607
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funzione JsIsRuntimeExecutionDisabled
Restituisce un valore che indica se l'esecuzione di script è disabilitata nel runtime.  
  
## Sintassi  
  
```vb  
STDAPI_(JsErrorCode) JsIsRuntimeExecutionDisabled(  
    _In_ JsRuntimeHandle runtime,  
    _Out_ bool *isDisabled  
);  
```  
  
#### Parametri  
 `runtime`  
 Specifica il controllo da parte del runtime in caso di disabilitazione dell'esecuzione.  
  
 `isDisabled`  
 `true` se l'esecuzione è disabilitata, in caso contrario, `false`.  
  
## Valore restituito  
 `JsNoError` se l'operazione ha esito positivo; in caso contrario, un codice di errore.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)