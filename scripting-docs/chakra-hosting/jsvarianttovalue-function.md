---
title: "Funzione JsVariantToValue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsVariantToValue"
helpviewer_keywords: 
  - "JsVariantToValue (funzione)"
ms.assetid: e8f9eb8b-55b3-4b65-927e-cad5b482edee
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsVariantToValue
Crea un valore JavaScript che è la proiezione dell’oggetto passato in `VARIANT`.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsVariantToValue(  
   _In_ VARIANT *variant,  
   _Out_ JsValueRef *value  
);  
```  
  
#### Parametri  
 `variant`  
 Oggetto `VARIANT` da proiettare.  
  
 `value`  
 Valore JavaScript che è la proiezione di `VARIANT`.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Il valore previsto utilizzabile tramite script per chiamare un oggetto di automazione COM da script.  Gli host sono responsabili per l'applicazione delle regole di threading COM.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)