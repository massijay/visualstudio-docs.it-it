---
title: "Funzione JsSerializeScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSerializeScript"
helpviewer_keywords: 
  - "JsSerializeScript (funzione)"
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione JsSerializeScript
Serializza uno script analizzato in un buffer che è possibile riusare.  
  
## Sintassi  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### Parametri  
 `script`  
 Script da serializzare.  
  
 `buffer`  
 Buffer in cui inserire lo script serializzato.  Può essere null.  
  
 `bufferSize`  
 In ingresso, le dimensioni del buffer in byte. In uscita, le dimensioni del buffer, in byte, necessarie per contenere lo script serializzato.  
  
## Valore restituito  
 Il codice `JsNoError` se l'operazione ha avuto esito positivo. In caso contrario, un codice di errore.  
  
## Note  
 `JsSerializeScript` analizza uno script, quindi archivia il form analizzato dello script in un formato indipendente dal runtime.  Lo script serializzato può essere deserializzato in qualsiasi runtime senza dover eseguire di nuovo l'analisi.  
  
 Richiede un contesto di script attivo.  
  
## Requisiti  
 **Intestazione:** jsrt.h  
  
## Vedere anche  
 [Riferimenti \(Runtime JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)