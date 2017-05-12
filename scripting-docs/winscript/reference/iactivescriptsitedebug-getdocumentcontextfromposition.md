---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
Utilizzato dal motore di linguaggio delegare `IDebugCodeContext::GetSourceContext`.  
  
## Sintassi  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parametri  
 `dwSourceContext`  
 \[in\] il contenuto di origine direttamente a `ParseScriptText` o a `AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] a inizio dell'offset del carattere del blocco di script o di scriptlet.  
  
 `uNumChars`  
 \[in\] numero di caratteri in questo contesto.  
  
 `ppsc`  
 \[out\] il contesto del documento che corrisponde a questo intervallo di posizione del carattere.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 I motori di linguaggio utilizzano questo metodo delegare `IDebugCodeContext::GetSourceContext`.  
  
## Vedere anche  
 [Interfaccia IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)