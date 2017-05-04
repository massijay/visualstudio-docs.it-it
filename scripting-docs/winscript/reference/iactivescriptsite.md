---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptSite"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
Implementato dall'host per creare un sito per il modulo di gestione di script di windows.  In genere, questo sito verrà associato al contenitore di tutti gli oggetti che sono visibili allo script, ad esempio i controlli ActiveX\).  In genere, questo contenitore corrisponderà al documento o alla pagina che viene visualizzata.  Microsoft Internet Explorer, ad esempio, creerebbe tale contenitore per ogni pagina HTML visualizzato.  Ogni controllo ActiveX \(o altri oggetti ActiveX\) nella pagina e il motore di scripting stesso, verrebbero enumerabile nel contenitore.  
  
## Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Recupera l'identificatore impostazioni locali dell'host per visualizzare gli elementi dell'interfaccia utente.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Ottiene informazioni su un elemento aggiunto a un modulo con una chiamata al metodo [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Recupera una stringa definita host che identifica in modo univoco la versione del documento corrente dal punto di vista dell'host.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Chiamato quando lo script termina l'esecuzione.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|All'host che il motore di script modificato gli stati.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|All'host che un errore di esecuzione si verifica quando il motore l'esecuzione dello script.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|All'host che il motore di scripting ha avviato il codice di script.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|All'host che il motore di scripting ha restituito dal codice di script.|  
  
## Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)