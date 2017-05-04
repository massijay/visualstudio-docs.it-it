---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
Induce il motore di script per annullare qualsiasi script attualmente caricato, per evitare perdite il relativo stato e rilasciare eventuali puntatori a interfaccia che deve altri oggetti, pertanto immettendo in uno stato chiuso.  I sink di evento, il testo viene eseguito lo script e le macro chiamate in corso vengono completati prima delle modifiche dello stato \(l'utilizzo [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) annullare un thread in esecuzione dello script\).  Questo metodo deve essere chiamato dall'host creando prima che l'interfaccia viene rilasciata per evitare problemi di riferimento circolare.  
  
## Sintassi  
  
```  
HRESULT Close(void);  
```  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore|Significato|  
|------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di script era già stato chiuso\).|  
|`OLESCRIPT_S_PENDING`|Il metodo è stata accodata correttamente, ma lo stato non è stato ancora.  Quando i cambiamenti di stato, il sito è necessario chiamare nuovamente il metodo [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md).|  
|`S_FALSE`|Il metodo corretto, ma lo script è già stato chiuso.|  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)