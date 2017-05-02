---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
Aggiunge uno scriptlet di codice come figlio dell'oggetto livello radice `IScriptNode`.  Nell'host, il nome completo di scriptlet può avere solo due livelli.  
  
## Sintassi  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Parametri  
 `pszDefaultName`  
 \[in\] indirizzo del nome predefinito da associare allo scriptlet.  
  
 `pszCode`  
 \[in\] indirizzo del testo di scriptlet.  
  
 `pszItemName`  
 \[in\] indirizzo del buffer dell'identificatore di primo livello del nome completo di scriptlet nell'host.  
  
 `pszSubItemName`  
 \[in\] indirizzo del buffer dell'identificatore di secondo livello del nome completo di scriptlet nell'host.  Set FROM NULL se il nome è un solo livello.  
  
 `pszEventName`  
 \[in\] indirizzo di un buffer che contiene il nome di evento per il quale lo scriptlet è un gestore eventi.  
  
 `pszDelimiter`  
 \[in\] indirizzo del delimitatore di entità finale\-de\-script\- blocco.  Quando `pszCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per individuare la fine del blocco di script.  Impostare questo parametro SU NULL se un delimitatore non contrassegna la fine del blocco di script.  
  
 `dwCookie`  
 \[in\] un valore definito dall'applicazione viene utilizzato per associare lo scriptlet con un oggetto host.  
  
 `dwFlags`  
 \[in\] Non utilizzato.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)