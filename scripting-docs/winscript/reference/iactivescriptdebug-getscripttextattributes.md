---
title: "IActiveScriptDebug::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptTextAttributes"
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptTextAttributes
Restituisce gli attributi di testo da un blocco arbitrario di testo dello script.  
  
## Sintassi  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Parametri  
 `pstrCode`  
 \[in\] il testo del blocco di script.  Questa stringa non sia con terminazione null.  
  
 `uNumCodeChars`  
 \[in\] numero di caratteri nel testo del blocco di script.  
  
 `pstrDelimiter`  
 \[in\] indirizzo del delimitatore di entità finale\-de\-script\- blocco.  Quando `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per individuare la fine del blocco di script.  Questo parametro specifica il delimitatore che l'host utilizzato, consentendo al motore di scripting fornire la pre\-elaborazione condizionale \(ad esempio, sostituendo una virgoletta \['\] con due virgolette semplici da utilizzare come delimitatore\).  Normalmente \(e\) se il motore di scripting utilizza queste informazioni dipendono dal motore di scripting.  Impostare questo parametro SU NULL se l'host non utilizzi un delimitatore per contrassegnare la fine del blocco di script.  
  
 `dwFlags`  
 \[in\] i flag associata al blocco di script.  Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|GETATTRTYPE\_DEPSCAN|0x0001|Indica rispettivamente che gli identificatori gli operatori e il punto devono essere identificati con flag di SOURCETEXT\_ATTR\_MEMBERLOOKUP e di SOURCETEXT\_ATTR\_IDENTIFIER.|  
|GETATTRFLAG\_THIS|0x0100|Indica che l'identificatore per l'oggetto corrente deve essere identificata con il flag di SOURCETEXT\_ATTR\_THIS.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|Indica che il contenuto e il testo del commento della stringa devono essere individuate con il flag di SOURCETEXT\_ATTR\_HUMANTEXT.|  
  
 `pattr`  
 \[in, out\] buffer per contenere gli attributi restituiti.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Uno SmartHost che implementa l'interfaccia `IDebugDocumentText` possibile utilizzare questo metodo delegare chiama il metodo `IDebugDocumentText::GetText`.  
  
 Questo metodo dai blocchi di script, il metodo `GetScriptletTextAttributes` riguarda gli scriptlets.  
  
## Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)