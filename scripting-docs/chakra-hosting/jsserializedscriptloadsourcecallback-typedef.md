---
title: "Typedef JsSerializedScriptLoadSourceCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Typedef JsSerializedScriptLoadSourceCallback
Chiamata di runtime per caricare codice sorgente dello script serializzato. Il chiamante deve mantenere il buffer dello script valido fino a `JsSerializedScriptUnloadCallback`.  
  
## Sintassi  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### Parametri  
 `sourceContext`  
 Contesto passato a `JsParseSerializedScriptWithCallback` o a `JsRunSerializedScriptWithCallback`.  
  
 `scriptBuffer`  
 Script restituito.  
  
## Note  
  
> [!WARNING]
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)