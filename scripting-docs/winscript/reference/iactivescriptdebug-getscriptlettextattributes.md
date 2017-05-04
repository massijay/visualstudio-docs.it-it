---
title: "IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.GetScriptletTextAttributes
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::GetScriptletTextAttributes"
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::GetScriptletTextAttributes
Restituisce gli attributi di testo per uno scriptlet arbitrario.  
  
## Sintassi  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### Parametri  
 `pstrCode`  
 \[in\] il testo di scriptlet.  Questa stringa non sia con terminazione null.  
  
 `uNumCodeChars`  
 \[in\] numero di caratteri del testo di scriptlet.  
  
 `pstrDelimiter`  
 \[in\] indirizzo di entità finale\- de \- scriptlet delimiter.  Quando `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per rilevare la fine dello scriptlet.  Questo parametro specifica il delimitatore che l'host utilizzato, consentendo al motore di scripting fornire la pre\-elaborazione condizionale \(ad esempio, sostituendo una virgoletta \['\] con due virgolette semplici da utilizzare come delimitatore\).  Normalmente \(e\) se il motore di scripting utilizza queste informazioni dipendono dal motore di scripting.  Impostare questo parametro SU NULL se l'host non utilizzi un delimitatore per contrassegnare la fine dello scriptlet.  
  
 `dwFlags`  
 \[in\] contrassegni associati allo scriptlet.  Può essere una combinazione dei valori seguenti:  
  
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
  
 Questa chiamata viene fornita perché gli scriptlets tendono a essere espressioni e possono disporre di una sintassi diversa da un blocco di script.  Se hanno la stessa sintassi, l'implementazione di questo metodo sarà identica all'implementazione del metodo `GetScriptTextAttributes`.  
  
## Vedere anche  
 [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Interfaccia IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Enumerazione SOURCE\_TEXT\_ATTR](../../winscript/reference/source-text-attr-enumeration.md)