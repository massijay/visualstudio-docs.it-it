---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo SetProperty, Interfaccia IActiveScriptProperty"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
Impostare la proprietà specificata dal parametro.  
  
## Sintassi  
  
```  
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### Parametri  
 `dwProperty`  
 Valore della proprietà da impostare.  
  
 `pvarIndex`  
 Non utilizzato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 I valori consentiti per `dwProperty` sono descritti nella tabella seguente.  
  
|Costante|Valore|Significato|  
|--------------|------------|-----------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Induce il motore di script per sta in modalità Integer anziché la modalità a virgola mobile.  Il valore predefinito è `False`.|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|Consente la stringa confrontare la funzione del motore di script da sostituire.|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|Notifica al motore di gestione di script che nessun altro modulo di gestione di script esiste per consentire all'oggetto globale.|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|Induce il motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] per selezionare un set di funzionalità di linguaggio da supportare.  Il set predefinito di funzionalità del linguaggio supportato dal motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è equivalente alla funzionalità del linguaggio impostata che è presente nella versione 5,7 del motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
  
## Note  
 Per abilitare o disabilitare divisione di interi, richiamare `SetProperty` e convertire `Boolean` a `Object`.  Per impostazione predefinita, il valore della proprietà è `False`.  Se impostato su `True`, operazioni di divisione restituirà solo Integer.  
  
 Per abilitare o disabilitare confronto di stringhe personalizzato, come `SetProperty` e sessione in un valore `Object`.  L'oggetto passato a deve implementare l'interfaccia [Interfaccia IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md).  Il metodo [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) dell'interfaccia [Interfaccia IActiveScriptStringCompare](../../winscript/reference/iactivescriptstringcompare-interface.md) viene chiamato ogni volta che una stringa confronta la funzione viene eseguita.  
  
 Per selezionare l'insieme di funzionalità di linguaggio per supportare quando il motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] viene inizializzato, richiamare `SetProperty` e passare un valore corrispondente alla funzionalità del linguaggio impostata per essere abilitato per SCRIPTPROP\_INVOKEVERSIONING.  Se questa proprietà è impostata su 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), le funzionalità del linguaggio disponibili sono uguali ad esempio quelli presenti nella versione 5,7 del motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Se è impostato su 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), le funzionalità del linguaggio disponibili sono quelle presenti nella versione 5,7 oltre alle nuove funzionalità aggiunte nella versione 5,8.  Per impostazione predefinita, questa proprietà è impostata su 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), che equivale alla funzionalità del linguaggio impostata che è presente nella versione 5,7, a meno che l'host supporta un comportamento predefinito diverso.  Ad esempio, Internet Explorer 8 selezionare le funzionalità del linguaggio [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] supportate dal motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] versione 5,8 per impostazione predefinita quando la modalità di documento predefinito per Internet Explorer 8 è "modalità di standard Internet Explorer 8".  Passando la modalità di documento Internet Explorer 8 alla modalità di standard o di peculiarità Internet Explorer 7 reimposta il motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] solo per supportare la funzionalità del linguaggio impostata esistente nel motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] la versione 5,7.  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING deve essere impostata solo quando il motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] di inizializzazione.  
  
## Esempio  
 Di seguito viene illustrato come determinare il motore di script per utilizzare divisione di interi e come consentire overload della funzione di confronto.  
  
```csharp  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## Vedere anche  
 [Definizione di compatibilità di documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)