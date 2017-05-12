---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
Recupera una stringa definita host che identifica in modo univoco la versione del documento corrente.  Se il documento è stato modificato correlato a l script windows \(come nel caso di una pagina HTML che viene modificata con Blocco Note\), il motore di scripting può salvare questo con il relativo stato persistente, forzando una ricompilazione la volta successiva che lo script venga caricato.  
  
## Sintassi  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### Parametri  
 `pstrVersionString`  
 \[out\] indirizzo della stringa host definita la versione del documento.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_NOTIMPL` se questo metodo non è supportato.  
  
## Note  
 Se `E_NOTIMPL` viene restituito, il motore di scripting deve presupporre che lo script venga sincronizzato con il documento.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)