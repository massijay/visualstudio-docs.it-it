---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
Restituisce gli attributi di testo da un blocco di script.  
  
## Sintassi  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### Parametri  
 `pszCode`  
 \[in, size\_is \(`cch`\)\] Il testo del blocco di script.  Questa stringa non sia con terminazione null.  
  
 `cch`  
 \[in\] dimensione utilizzata per i parametri `pattr` e `pszCode`.  
  
 `pszDelimiter`  
 \[in\] indirizzo del delimitatore di fine script.  Quando `pszCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per rilevare la fine dello scriptlet.  Impostare questo parametro SU NULL se non c'è delimitatore per identificare la fine del blocco di script.  
  
 `dwFlags`  
 \[in\] i flag associati agli attributi di testo del blocco di script.  Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Identificare gli identificatori che presentano l'attributo di SOURCETEXT\_ATTR\_IDENTIFIER e identificare gli operatori del punto che presentano l'attributo di SOURCETEXT\_ATTR\_MEMBERLOOKUP.|  
|GETATTRFLAG\_THIS|0x0100|Identificare l'oggetto corrente con l'attributo di SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Individuare il contenuto e il testo del commento della stringa con l'attributo di SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out, size\_is `cch`\)\] Informazioni sui colori per il codice dei blocchi di script.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)