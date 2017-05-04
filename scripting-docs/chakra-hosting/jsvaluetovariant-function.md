---
title: "Funzione JsValueToVariant | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant (funzione)"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsValueToVariant
Inizializza l'oggetto passato in `VARIANT` come proiezione di un valore JavaScript.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### Parametri  
 `object`  
 Valore JavaScript nel progetto come `VARIANT`.  
  
 `variant`  
 Puntatore a uno struct `VARIANT` che verrà inizializzato come proiezione.  
  
## Valore restituito  
  
## Note  
 La proiezione `VARIANT` può essere utilizzata dai client di automazione COM per effettuare una chiamata nell'oggetto JavaScript proiettato.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)