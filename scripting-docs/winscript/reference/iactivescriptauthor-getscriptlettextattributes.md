---
title: "IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptletTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptletTextAttributes"
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::GetScriptletTextAttributes
Restituisce gli attributi di testo di una scriptlet.  
  
## Sintassi  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### Parametri  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] il testo di scriptlet.  Questa stringa non sia con terminazione null.  
  
 `cch`  
 \[in\] dimensione utilizzata per i parametri `pattr` e `pszCode`.  
  
 `pszDelimiter`  
 \[in\] indirizzo di entità finale\- de \- scriptlet delimiter.  Quando `pszCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per rilevare la fine dello scriptlet.  Impostare questo parametro SU NULL se nessun delimitatore viene utilizzato per identificare la fine dello scriptlet.  
  
 `dwFlags`  
 \[in\] i flag associati agli attributi del testo di scriptlet.  Può essere una combinazione dei valori seguenti.  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Identificare gli identificatori che presentano l'attributo di SOURCETEXT\_ATTR\_IDENTIFIER e identificare gli operatori del punto che presentano l'attributo di SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Identificare l'oggetto corrente con l'attributo di SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Individuare il contenuto e il testo del commento della stringa con l'attributo di SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out, size\_is `cch`\)\] Informazioni sui colori per il codice di scriptlet.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)