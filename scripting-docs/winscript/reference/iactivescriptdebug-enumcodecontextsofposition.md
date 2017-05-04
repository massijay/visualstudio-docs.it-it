---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
Utilizzato da uno SmartHost delegare il metodo `IDebugDocumentContext::EnumCodeContexts`.  
  
## Sintassi  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Parametri  
 `dwSourceContext`  
 \[in\] il contesto di origine direttamente a `IActiveScriptParse::ParseScriptText` o a `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] a inizio dell'offset del carattere del testo dello script.  
  
 `uNumChars`  
 \[in\] numero di caratteri in questo contesto.  
  
 `ppescc`  
 \[out\] enumeratore i contesti di codice nell'intervallo specificato.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Gli SmartHost utilizzano questo metodo delegare il metodo `IDebugDocumentContext::EnumCodeContexts`.  
  
## Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)