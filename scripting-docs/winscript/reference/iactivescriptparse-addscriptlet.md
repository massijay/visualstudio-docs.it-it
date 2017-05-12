---
title: "IActiveScriptParse::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_AddScriptlet"
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse::AddScriptlet
Aggiunge uno scriptlet di codice allo script.  Questo metodo viene utilizzato in ambienti in cui lo stato persistente lo script è intrecciato con il documento host e l'host è responsabile del ripristino dello script, anziché tramite un'interfaccia `IPersist*`.  Gli esempi primari sono linguaggi di script HTML che consentono scriptlets del codice incorporate nel documento HTML da associare agli intrinseci \(ad esempio, ONCLICK\= " button1.text\='Exit"\).  
  
## Sintassi  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### Parametri  
 `pstrDefaultName`  
 \[in\] indirizzo di un nome predefinito da associare allo scriptlet.  Se lo scriptlet non contiene denominare le informazioni \(come nell'esempio di ONCLICK precedente\), questo nome verrà utilizzato per identificare lo scriptlet.  Se questo parametro è `NULL`, il motore di scripting fabbrica un nome univoco, se necessario.  
  
 `pstrCode`  
 \[in\] indirizzo del testo di scriptlet da aggiungere.  L'interpretazione di questa stringa dipende dal linguaggio di script.  
  
 `pstrItemName`  
 \[in\] indirizzo di un buffer che contiene il nome dell'elemento associato a questo scriptlet.  Questo parametro, oltre a `pstrSubItemName`, identificare l'oggetto per il quale lo scriptlet è un gestore eventi.  
  
 `pstrSubItemName`  
 \[in\] indirizzo di un buffer che contiene il nome `subobject` dell'elemento denominato con cui questo scriptlet associato, questo nome deve essere trovato nelle informazioni di tipo denominate dell'elemento.  Questo parametro è NULL se lo scriptlet deve essere associato all'elemento denominato anziché `subitem`.  Questo parametro, oltre a `pstrItemName`, identificare l'oggetto specifico per il quale lo scriptlet è un gestore eventi.  
  
 `pstrEventName`  
 \[in\] indirizzo di un buffer che contiene il nome dell'evento per il quale lo scriptlet è un gestore eventi.  
  
 `pstrDelimiter`  
 \[in\] indirizzo di entità finale\- de \- scriptlet delimiter.  Quando il parametro `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per rilevare la fine dello scriptlet.  Questo parametro specifica il delimitatore che l'host utilizzato, consentendo al motore di scripting fornire la pre\-elaborazione condizionale \(ad esempio, sostituendo una virgoletta \['\] con due virgolette semplici da utilizzare come delimitatore\).  Normalmente \(e\) se il motore di scripting utilizza queste informazioni dipendono dal motore di scripting.  Impostare questo parametro SU NULL se l'host non utilizzi un delimitatore per contrassegnare la fine dello scriptlet.  
  
 `dwSourceContextCookie`  
 \[in\] valore definito dall'applicazione viene utilizzato per eseguire il debug.  
  
 `ulStartingLineNumber`  
 \[in\] il valore in base zero che specifica tale matrice l'analisi inizierà a.  
  
 `dwFlags`  
 \[in\] contrassegni associati allo scriptlet.  Può essere una combinazione dei valori seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|SCRIPTTEXT\_ISVISIBLE|Indica che il testo dello script è visibile \(e, pertanto, essere chiamato per nome\) come metodo globale nello spazio dei nomi dello script.|  
|SCRIPTTEXT\_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato quando il motore di scripting viene salvato, ad esempio tramite una chiamata a `IPersist*::Save`\), o se il motore di scripting viene reimpostato tramite una transizione di nuovo allo stato inizializzato.  Per ulteriori informazioni su questo stato, vedere gli stati del modulo di gestione di script.|  
  
 `pbstrName` ,  
 \[out\] nome effettivo utilizzato per identificare lo scriptlet.  Si tratta di essere di preferenza: un nome specificato in modo esplicito nel testo di scriptlet, il nome predefinito in `pstrDefaultName`, o un nome univoco sintetizzato nel motore di scripting.  
  
 `pexcepinfo` ,  
 \[out\] indirizzo di una struttura che contiene informazioni sull'eccezione.  Questa struttura deve essere soddisfatta se DISP\_E\_EXCEPTION viene restituito.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`DISP_E_EXCEPTION`|Un'eccezione è stata apportata nella traccia dello scriptlet.  Il parametro `pexcepinfo` contiene informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_NOTIMPL`|Questo metodo non è supportato; il motore di scripting non supporta l'aggiunta che vengono creati i sink gli scriptlets.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\) e pertanto non è stata avuto esito negativo.|  
|`OLESCRIPT_E_INVALIDNAME`|Il nome predefinito non è valido in questo linguaggio di script.|  
|`OLESCRIPT_E_SYNTAX`|Un errore di sintassi non specificato si è verificato in scriptlet.|  
  
## Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)