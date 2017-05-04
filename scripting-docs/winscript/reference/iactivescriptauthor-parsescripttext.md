---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
Analizza il testo dello script, aggiungere testo al motore di creazione di script e crea un oggetto `IScriptEntry` che corrisponde al blocco di script.  
  
## Sintassi  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Parametri  
 `pszCode`  
 \[in\] il testo dello script da analizzare.  
  
 `pszItemName`  
 \[in\] indirizzo del buffer contenente il nome dell'elemento associato al blocco di script.  
  
 `pszDelimiter`  
 \[in\] indirizzo del delimitatore di entità finale\-de\-script\- blocco.  Quando `pszCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per individuare la fine del blocco di script.  Impostare questo parametro SU NULL se non c'è delimitatore per identificare la fine del blocco di script.  
  
 `dwCookie`  
 \[in\] un valore definito dall'applicazione associato al nuovo oggetto `IScriptEntry`.  
  
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