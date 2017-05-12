---
title: "IActiveScriptParse::InitNew | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.InitNew
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_InitNew"
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::InitNew
Inizializza il motore di scripting.  
  
## Sintassi  
  
```  
HRESULT InitNew(void);  
```  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_FAIL` se si è verificato un errore durante l'inizializzazione.  
  
## Note  
 Prima che il motore di scripting possa essere utilizzato, uno dei seguenti metodi deve essere chiamato: `IPersist*::Load`, `IPersist*::InitNew`, o `IActiveScriptParse::InitNew`.  La semantica di questo metodo è identica a `IPersistStreamInit::InitNew`, in quanto questo metodo indica al motore di scripting di inizializzarsi.  Si noti che non è valida chiamare sia `IPersist*::InitNew` o `IActiveScriptParse::InitNew` che `IPersist*::Load`, né è valida chiamare più volte `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, o `IPersist*::Load`.  
  
## Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)