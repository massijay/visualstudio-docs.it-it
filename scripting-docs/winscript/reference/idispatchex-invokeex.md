---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo InvokeEx"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
Fornisce l'accesso a proprietà e metodi esposti da un oggetto `IDispatchEx`.  
  
## Sintassi  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### Parametri  
 `id`  
 Identifica il membro.  Utilizzare `GetDispID` o `GetNextDispID` ottenere l'identificatore di invio.  
  
 `lcid`  
 Contesto di impostazioni locali all'interno del quale devono essere interpretati gli argomenti.  `lcid` viene passato a `InvokeEx` per consentire all'interpretazione dei relativi argomenti specifici delle impostazioni locali.  
  
 `wFlags`  
 i valori consentiti per `wFlags` sono:  
  
 DISPATCH\_PROPERTYGET &#124; DISPATCH\_METHOD &#124; DISPATCH\_PROPERTYPUT &#124; DISPATCH\_PROPERTYPUTREF &#124; DISPATCH\_CONSTRUCT  
  
 Flag che descrivono il contesto di chiamata `InvokeEx` :  
  
|Valore|Significato|  
|------------|-----------------|  
|DISPATCH\_METHOD|Il membro viene richiamato il metodo.  Se una proprietà ha lo stesso nome, che questo sia il flag di DISPATCH\_PROPERTYGET può essere impostata su \(definito da `IDispatch`\).|  
|DISPATCH\_PROPERTYGET|Il membro viene recuperato come una proprietà o membro dati \(definito da `IDispatch`\).|  
|DISPATCH\_PROPERTYPUT|Il membro viene modificato come una proprietà o membro dati \(definito da `IDispatch`\).|  
|DISPATCH\_PROPERTYPUTREF|Il membro viene modificato mediante l'assegnazione di riferimento anziché l'assegnazione di un valore.  Questo flag è valido solo quando la proprietà accetta un riferimento a un oggetto \(definito da `IDispatch`\).|  
|DISPATCH\_CONSTRUCT|Il membro viene utilizzato come costruttore.  \(Si tratta di un nuovo valore definito da `IDispatchEx`\).  i valori consentiti per `wFlags` sono:<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 Puntatore a una struttura contenente una matrice di argomenti, una matrice di DISPID per argomenti denominati e i conteggi del numero di elementi nelle matrici.  Vedere la documentazione `IDispatch` per una descrizione completa della struttura di DISPPARAMS.  
  
 `pVarRes`  
 Puntatore alla posizione in cui il risultato è di essere archiviato o null se il chiamante non prevede risultato.  In questo argomento viene ignorato se DISPATCH\_PROPERTYPUT o DISPATCH\_PROPERTYPUTREF è specificato.  
  
 `pei`  
 Puntatore a una struttura contenente informazioni sull'eccezione.  Questa struttura deve essere soddisfatta se `DISP_E_EXCEPTION` viene restituito.  Può essere null.  Vedere la documentazione `IDispatch` per una descrizione completa della struttura `EXCEPINFO`.  
  
 `pspCaller`  
 Puntatore a un oggetto del provider di servizi forniti dal chiamante, che consente all'oggetto per ottenere i servizi dal chiamante.  Può essere null.  
  
 `IDispatchEx::InvokeEx` fornisce tutte le funzionalità `IDispatch::Invoke` e aggiungere alcune estensioni:  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|Indica che l'elemento viene utilizzato come costruttore.|  
|`pspCaller`|`pspCaller` consente l'accesso dell'oggetto servizi forniti dal chiamante.  I servizi specifici possono essere gestiti dal chiamante stesso o essere delegati i chiamanti ulteriormente nella catena di chiamate.  Ad esempio, se un modulo di gestione di script in un browser effettua una chiamata `InvokeEx` a un oggetto esterno, l'oggetto può seguire la catena `pspCaller` per ottenere i servizi dal modulo di gestione di script o dal browser.  Notare che la catena di chiamate non corrisponde alla catena \- anche di creazione nota come la catena del contenitore o la catena del sito.  La catena di creazione può essere disponibile tramite un altro meccanismo come `IObjectWithSite`\).|  
|Puntatore di`this`|Quando DISPATCH\_METHOD viene impostato in `wFlags`, potrebbe essere "un parametro denominato" for "this" valore.  Il DISPID verrà DISPID\_THIS e deve essere il primo parametro denominato.|  
  
 Il parametro inutilizzato `riid` in `IDispatch::Invoke` è stato rimosso.  
  
 Il parametro `puArgArr` in `IDispatch::Invoke` è stato rimosso.  
  
 Vedere la documentazione `IDispatch::Invoke` per i seguenti esempi:  
  
 "Chiamando un metodo senza argomenti"  
  
 "Ottenere e impostare le proprietà"  
  
 "Passaggio di parametri"  
  
 "Proprietà indicizzate"  
  
 "Generazione di eccezioni durante la chiamata"  
  
 "Restituendo gli errori"  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|||  
|-|-|  
|`S_OK`|Riuscita.|  
|DISP\_E\_BADPARAMCOUNT|Il numero di elementi fornito in DISPPARAMS è diverso dal numero di argomenti accettati dal metodo o la proprietà.|  
|DISP\_E\_BADVARTYPE|Uno degli argomenti in `rgvarg` non è un tipo di variant valido.|  
|DISP\_E\_EXCEPTION|L'applicazione deve generare un'eccezione.  In questo caso, la struttura passata in `pei` deve essere soddisfatta.|  
|DISP\_E\_MEMBERNOTFOUND|Il membro richiesto non esiste, o la chiamata a `InvokeEx` ha tentato di impostare il valore di una proprietà di sola lettura.|  
|DISP\_E\_NONAMEDARGS|Questa implementazione `IDispatch` non supporta gli argomenti predefiniti.|  
|DISP\_E\_OVERFLOW|Uno degli argomenti in `rgvarg` non può essere assegnato al tipo specificato.|  
|DISP\_E\_PARAMNOTFOUND|Uno dei Dispid non corrisponde a un parametro nel metodo.|  
|DISP\_E\_TYPEMISMATCH|Uno o più argomenti non possono essere assegnati.|  
|DISP\_E\_UNKNOWNLCID|Il membro richiamato interpreta gli argomenti di tipo stringa come LCID e LCID non è riconosciuto.  Se l'LCID non è necessario per interpretare gli argomenti, non si dovrebbe verificare questo errore.|  
|DISP\_E\_PARAMNOTOPTIONAL|È stato omesso un parametro obbligatorio.|  
  
## Esempio  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)