---
title: "Typedef JsNativeFunction | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Typedef JsNativeFunction
Callback di funzione.  
  
## Sintassi  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### Parametri  
 callee  
 Oggetto `Function` che rappresenta la funzione richiamata.  
  
 isConstructCall  
 Indica se si tratta di una chiamata normale o di una "nuova" chiamata.  
  
 arguments  
 Argomenti della chiamata.  
  
 argumentCount  
 Numero di argomenti.  
  
## Valore proprietà\/Valore restituito  
 Risultato della chiamata, se presente.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)