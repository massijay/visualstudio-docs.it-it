---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
Restituisce lo scriptlet con gli attributi specificati.  
  
## Sintassi  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parametri  
 `pdisp`  
 \[in\] l'oggetto `IDispatch` che corrisponde a `NamedItem` a esso scriptlet è collegato.  
  
 `pszItem`  
 \[in\] indirizzo del buffer dell'identificatore di primo livello del nome completo di scriptlet nell'host.  
  
 `pszSubItem`  
 \[in\] indirizzo del buffer dell'identificatore di secondo livello del nome completo di scriptlet nell'host.  Set FROM NULL se il nome è un solo livello.  
  
 `pszEvent`  
 \[in\] indirizzo di un buffer che contiene il nome dell'evento.  Lo scriptlet è un gestore eventi per l'evento.  
  
 `ppse`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore a un'interfaccia `IScriptEntry` di scriptlet con gli attributi specificati.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)