---
title: "IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptParseProcedureOld::ParseProcedureText"
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptParseProcedureOld::ParseProcedureText
Analizzare il codice di creazione specificato e aggiunge una routine anonima allo spazio dei nomi.  
  
## Sintassi  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### Parametri  
 `pstrCode`  
 \[in\] il testo della routine da valutare.  L'interpretazione di questa stringa dipende dal linguaggio di script.  
  
 `pstrFormalParams`  
 \[in\] nomi di parametro formale per la routine.  I nomi dei parametri devono essere separati da delimitatori appropriati per il modulo di gestione di script.  I nomi non devono essere racchiusi tra parentesi.  
  
 `pstrItemName`  
 \[in\] il nome dell'elemento denominato che fornisce il contesto in cui la routine deve essere valutata.  Se questo parametro è `NULL`, il codice viene valutato nel contesto globale del motore di scripting.  
  
 `punkContext`  
 \[in\] l'oggetto di contesto.  Questo oggetto è riservato da utilizzare in un ambiente di debug, in cui tale contesto può essere fornito dal debugger per rappresentare un contesto di esecuzione attivo.  Se questo parametro è `NULL`, il motore utilizza `pstrItemName` per identificare il contesto.  
  
 `pstrDelimiter`  
 \[in\] il delimitatore di fine della routine.  Quando `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per rilevare la fine della routine.  Questo parametro specifica il delimitatore che l'host utilizzato, consentendo al motore di scripting fornire un determinato condizionale, pre\-elaborazione primitiva \(ad esempio, sostituendo una virgoletta \['\] con due virgolette semplici da utilizzare come delimitatore\).  Normalmente \(e\) se il motore di scripting utilizza queste informazioni dipendono dal motore di scripting.  Impostare questo parametro su `NULL` se l'host non utilizzi un delimitatore per contrassegnare la fine della routine.  
  
 `dwSourceContextCookie`  
 \[in\] valore definito dall'applicazione viene utilizzato per eseguire il debug.  
  
 `ulStartingLineNumber`  
 \[in\] valore in base zero che specifica alla riga l'analisi verrà avviato.  
  
 `dwFlags`  
 \[in\] i flag associati alla routine.  Può essere una combinazione di questi valori.  
  
|Costante|Valore|Significato|  
|--------------|------------|-----------------|  
|SCRIPTPROC\_ISEXPRESSION|0x00000020|Indica che il codice in `pstrCode` è un'espressione che rappresenta il valore restituito dalla routine.|  
|SCRIPTPROC\_IMPLICIT\_THIS|0x00000100|Indica che il puntatore `this` è incluso nella routine.|  
|SCRIPTPROC\_IMPLICIT\_PARENTS|0x00000200|Indica che i calcoli del puntatore `this` sono inclusi nella routine.|  
  
 `ppdisp`  
 \[out\] restituisce un wrapper di invio in cui il metodo predefinito è la routine analizzata da questo metodo.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_NOTIMPL`|Metodo non supportato.  Il motore di scripting non supporta l'aggiunta di runtime delle procedure allo spazio dei nomi.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting è stato inizializzato o chiuso\).|  
|`OLESCRIPT_E_SYNTAX`|Un errore di sintassi non si è verificata nella routine.|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto di invio; il parametro `ppdisp`è impostato su `NULL`.|  
  
## Note  
 Nessun codice di script vengono valutate durante questa chiamata, piuttosto, la routine viene compilata in un metodo su `ppdisp` in cui può essere chiamata dallo script successive.  
  
 Questa interfaccia è deprecata a favore dell'interfaccia `IActiveScriptParseProcedure`.  Il metodo `IActiveScriptParseProcedure::ParseProcedureText` è simile a questo metodo, ma consente il nome della routine da specificare.  In tutti i casi, `IActiveScriptParseProcedure::ParseProcedureText` deve essere utilizzato.  
  
## Vedere anche  
 [Interfaccia IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)