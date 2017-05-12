---
title: "IActiveScriptParseProcedure::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedure.ParseProcedureText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedure_ParseProcedureText"
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure::ParseProcedureText
Analizzare il codice di creazione specificato e aggiunge la routine allo spazio dei nomi.  
  
## Sintassi  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### Parametri  
 `pstrCode`  
 \[in\] indirizzo del testo della routine da valutare.  L'interpretazione di questa stringa dipende dal linguaggio di script.  
  
 `pstrFormalParams`  
 \[in\] indirizzo dei nomi di parametro formale per la routine.  I nomi dei parametri devono essere separati da delimitatori appropriati per il modulo di gestione di script.  I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrProcedureName`  
 \[in\] indirizzo il nome della routine da analizzare.  
  
 `pstrItemName`  
 \[in\] indirizzo del nome dell'elemento che fornisce il contesto in cui la routine deve essere valutata.  Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di scripting.  
  
 `punkContext`  
 \[in\] indirizzo dell'oggetto di contesto.  Questo oggetto è riservato da utilizzare in un ambiente di debug, in cui tale contesto può essere fornito dal debugger per rappresentare un contesto di esecuzione attivo.  Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 \[in\] indirizzo del delimitatore di fine della routine.  Quando `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per rilevare la fine della routine.  Questo parametro specifica il delimitatore che l'host utilizzato, consentendo al motore di scripting fornire la pre\-elaborazione condizionale \(ad esempio, sostituendo una virgoletta \['\] con due virgolette semplici da utilizzare come delimitatore\).  Normalmente \(e\) se il motore di scripting utilizza queste informazioni dipendono dal motore di scripting.  Impostare questo parametro su `NULL` se l'host non utilizzi un delimitatore per contrassegnare la fine della routine.  
  
 `dwSourceContextCookie`  
 \[in\] valore definito dall'applicazione viene utilizzato per eseguire il debug.  
  
 `ulStartingLineNumber`  
 \[in\] il valore in base zero che specifica tale matrice l'analisi inizierà a.  
  
 `dwFlags`  
 \[in\] i flag associati alla routine.  Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTPROC\_ISEXPRESSION|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito dalla routine.  Per impostazione predefinita, il codice può contenere un'espressione, un elenco di istruzioni, o qualsiasi altro elemento consentiti in una routine dal linguaggio di script.|  
|SCRIPTPROC\_IMPLICIT\_THIS|Indica che il puntatore `this` è incluso nella routine.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|Indica che i calcoli del puntatore `this` sono inclusi nella routine.|  
  
 `ppdisp`  
 \[out\] indirizzo del puntatore per l'oggetto che contiene metodi globali e le proprietà dello script.  Se il motore di scripting non supporta tale oggetto, `NULL` viene restituito.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_NOTIMPL`|Metodo non supportato.  Il motore di scripting non supporta l'aggiunta di runtime delle procedure allo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting è stato inizializzato o chiuso\).|  
|`OLESCRIPT_E_SYNTAX`|Un errore di sintassi non si è verificata nella routine.|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto di invio; il parametro `ppdisp` è impostato su `NULL`.|  
  
## Note  
 Nessun codice di script vengono valutate durante questa chiamata, piuttosto, la routine viene compilata in stato dello script in cui può essere chiamata dallo script successive.  
  
## Vedere anche  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)