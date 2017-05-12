---
title: "Funzione JsGetPropertyIdFromName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetPropertyIdFromName"
helpviewer_keywords: 
  - "JsGetPropertyIdFromName (funzione)"
ms.assetid: 1674906f-746a-4c62-99cd-023276683a86
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsGetPropertyIdFromName
Ottiene l'ID proprietà associato al nome.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsGetPropertyIdFromName(  
   _In_z_ const wchar_t *name,  
   _Out_ JsPropertyIdRef *propertyId  
);  
```  
  
#### Parametri  
 `name`  
 Nome dell'ID proprietà da ottenere o creare.  Il nome può essere costituito solo da cifre.  
  
 `propertyId`  
 ID proprietà nel runtime per il nome specificato.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 Gli ID proprietà sono specifici di un contesto e non possono essere usati tra contesti diversi.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)