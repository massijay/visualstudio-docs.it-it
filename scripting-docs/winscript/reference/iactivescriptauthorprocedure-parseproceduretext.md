---
title: "IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthorProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthorProcedure::ParseProcedureText"
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthorProcedure::ParseProcedureText
Analizza un codice di creazione, aggiungere il codice di creazione al motore di creazione di script e crea un oggetto `IScriptEntry` che corrisponde al codice di creazione.  
  
## Sintassi  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### Parametri  
 `pszCode`  
 \[in\] il testo dello script da analizzare.  
  
 `pszFormalParams`  
 \[in\] indirizzo dei nomi di parametro formale per la routine.  I nomi dei parametri devono essere separati da delimitatori appropriati per il motore di creazione di script.  I nomi non devono essere racchiusi in parentesi.  
  
 `pszProcedureName`  
 \[in\] indirizzo il nome della routine da analizzare.  
  
 `pszItemName`  
 \[in\] indirizzo del buffer contenente il nome dell'elemento associato all'oggetto `IScriptEntry`.  
  
 `pszDelimiter`  
 \[in\] indirizzo del delimitatore di entità finale\-de\-script\- blocco.  Quando `pszCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per individuare la fine del blocco di script.  Impostare questo parametro SU NULL se non c'è delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwCookie`  
 \[in\] un valore definito dall'applicazione associato al nuovo oggetto `IScriptEntry`.  
  
 `dwFlags`  
 \[in\] Non utilizzato.  
  
 `pdispFor`  
 \[in\] Non utilizzato.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Il modulo corrente [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] non implementa questo metodo.  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)