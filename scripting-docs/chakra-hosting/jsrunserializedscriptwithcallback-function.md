---
title: "funzione JsRunSerializedScriptWithCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# funzione JsRunSerializedScriptWithCallback
Esegue uno script serializzato. Fornisce la possibilità di eseguire caricamento lazy del codice script solo se\/quando è necessario.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### Parametri  
 `scriptLoadCallback`  
 Callback chiamato quando il codice sorgente dello script deve essere caricato.  
  
 `scriptUnloadCallback`  
 Callback chiamato quando lo script serializzato e il codice sorgente non sono più necessari.  
  
 `buffer`  
 Script serializzato.  
  
 `sourceContext`  
 Cookie che identifica lo script che può essere usato dai contesti di script sottoponibili a debug. Questo contesto verrà passato in scriptLoadCallback e scriptUnloadCallback.  
  
 `sourceUrl`  
 Percorso di origine dello script.  
  
 `result`  
 Risultato dell'esecuzione dello script, se disponibile. Questo parametro può essere null.  
  
## Valore restituito  
 Codice `JsNoError` se l'operazione ha avuto esito positivo; in caso contrario, un codice di errore.  
  
## Note  
  
> [!NOTE]
>  Questa API non è ancora disponibile per le app di Windows Store.  
  
 Richiede un contesto di script attivo.  
  
 Il runtime manterrà il buffer finché tutte le istanze di qualsiasi funzione creata dal buffer non vengono sottoposte a Garbage Collection.  Verrà quindi chiamato scriptUnloadCallback per informare il chiamante che è possibile eseguire il rilascio.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)