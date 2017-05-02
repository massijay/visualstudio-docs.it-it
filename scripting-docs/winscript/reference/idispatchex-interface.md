---
title: "Interfaccia IDispatchEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDispatchEx"
  - "Interfaccia IDispatchEx, Informazioni su IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Interfaccia IDispatchEx
`IDispatchEx`, un'estensione dell'interfaccia `IDispatch`, funzionalità supportate appropriate per i linguaggi dinamici quali linguaggi di script.  In questa sezione vengono descritte l'interfaccia stessa `IDispatchEx`, le differenze tra `IDispatch` e `IDispatchEx`e la logica alla base delle estensioni.  È opportuno che i reader hanno familiarità con `IDispatch` e abbiano accesso alla documentazione `IDispatch`.  
  
## Note  
 `IDispatch` è stato compilato essenzialmente per Microsoft Visual Basic.  La limitazione principale `IDispatch` è che presuppone che gli oggetti siano statici.  Ovvero poiché gli oggetti non cambiano in fase di esecuzione, le informazioni sul tipo è completamente descriverle in fase di compilazione.  Modelli dinamici di runtime rilevati nei linguaggi di script come scripting edition Visual Basic \(VBScript\) e [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e modelli a oggetti quali Dynamic HTML richiedono un'interfaccia più flessibile.  
  
 `IDispatchEx` è stato sviluppato per fornire a tutti i servizi `IDispatch` nonché di alcune estensioni appropriati per i linguaggi ad associazione tardiva più linguaggi dinamici quali script.  Funzionalità aggiuntive `IDispatchEx` oltre a quelle fornite da `IDispatch` sono:  
  
-   Aggiungere nuovi membri a un oggetto \("expando"\) — utilizzano `GetDispID` con il flag `fdexNameEnsure`.  
  
-   Eliminare i membri di un `DeleteMemberByName` di utilizzo o `DeleteMemberByDispID`.  
  
-   Operazione\- utilizzare con distinzione tra maiuscole e minuscole `fdexNameCaseSensitive` o `fdexNameCaseInsensitive`dispatch.  
  
-   Ricerca del membro con vettori di utilizzo implicito `fdexNameImplicit`.  
  
-   Enumerare i dispid di un utilizzo `GetNextDispID`.  
  
-   Mapping da DISPID a adottato per l'utilizzo `GetMemberName`dell'elemento.  
  
-   Ottenere le proprietà di membro\- utilizzo `GetMemberProperties`dell'oggetto.  
  
-   Chiamata al metodo con puntatore\- utilizzo `InvokeEx` `this` con DISPATCH\_METHOD.  
  
-   Abilitare i browser che supportano il concetto degli spazi dei nomi per ottenere il padre dello spazio dei nomi di un utilizzo `GetNameSpaceParent`.  
  
 Gli oggetti che supportano `IDispatchEx` potrebbero supportare anche `IDispatch` per compatibilità con le versioni precedenti.  La natura dinamica di oggetti che supportano alcune `IDispatchEx` ha implicazioni per l'interfaccia `IDispatch` di tali oggetti.  Ad esempio, `IDispatch` effettua la distinzione seguente:  
  
-   Il membro e il parametro Dispid devono rimanere costanti per la durata dell'oggetto.  Ciò consente a un client ottenere una volta Dispid e li memorizzare nella cache per un utilizzo successivo.  
  
 Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione dei membri, l'insieme dei dispid valido non rimane costante.  Tuttavia, `IDispatchEx` richiede che il mapping tra DISPID e il nome del membro rimanga costante.  Ciò significa che se un membro viene eliminata:  
  
-   Il DISPID non può essere riutilizzato finché creare un membro con lo stesso nome.  
  
-   Il DISPID deve rimanere valido per `GetNextDispID`.  
  
-   Il DISPID deve essere accettato correttamente da qualsiasi `IDispatch` o `IDispatchEx` che metodo deve riconoscere il membro come eliminato e restituire un codice di errore appropriato \(in genere DISP\_E\_MEMBERNOTFOUND o S\_FALSE\).  
  
## Esempi  
 Questo codice [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tracciatura func \(\) esegue le operazioni seguenti:  
  
-   Crea un nuovo oggetto chiamando il costruttore `Object` e assegna un puntatore al nuovo oggetto a Obj variabile.  
  
-   Crea un nuovo elemento denominato Elem nell'oggetto e assegna a questo elemento un puntatore a gatto di funzione.  
  
-   Chiama la funzione.  Poiché si sta chiamando il metodo, il puntatore `this` fa riferimento all'oggetto Obj.  La funzione viene aggiunto un nuovo elemento, barra, all'oggetto.  
  
 Il codice HTML completo è:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Un controllo inserito nella stessa pagina Web può ottenere un puntatore di invio al motore di script dal browser.  Il controllo può quindi distribuire l'analisi func \(\):  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Il codice dal controllo, test, il medesimo risultato della funzione `test()`di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Si noti che le chiamate di invio sono state trasformate il motore di esecuzione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e modificare lo stato del modulo:  
  
-   Ottiene il puntatore di invio alla funzione di gatto utilizzando `GetDispID()`.  
  
-   Ottiene il puntatore di invio alla funzione dell'oggetto utilizzando `GetDispID()`.  
  
-   Costruisce un oggetto chiamando la funzione dell'oggetto con `InvokeEx()` e ottiene un puntatore di invio all'oggetto appena creato.  
  
-   Crea un nuovo elemento, Elem, nell'oggetto utilizzando `GetDispID()` con il flag `fdexNameEnsure`.  
  
-   Posizionare il puntatore di invio a gatto nell'elemento utilizzando `InvokeEx()`.  
  
-   Chiama il puntatore di invio a gatto come metodo chiamando `InvokeEx()` e passare il puntatore di invio all'oggetto costruito quale il puntatore `this`.  
  
-   Il metodo di gatto creato un nuovo elemento, barra, sull'oggetto corrente `this`.  
  
-   Verifica che il nuovo elemento, barra, sia stato creato l'oggetto costruito l'enumerazione degli elementi utilizzando `GetNextDispID()`.  
  
 Il codice per il controllo del test:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## Metodi  
 [Metodi IDispatchEx](../../winscript/reference/idispatchex-methods.md)