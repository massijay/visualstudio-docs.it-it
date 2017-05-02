---
title: "typedef JsSerializedScriptUnloadCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# typedef JsSerializedScriptUnloadCallback
Chiamato dal runtime quando viene terminato con tutte le risorse correlate all'esecuzione di script. Il chiamante deve liberare l'origine se caricata, il codice byte e il contesto in questo momento.  
  
## Sintassi  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### Parametri  
 `sourceContext`  
 Contesto passato a `JsParseSerializedScriptWithCallback` o a `JsRunSerializedScriptWithCallback`.  
  
## Note  
  
> [!WARNING]
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)