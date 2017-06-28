---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo GetProperty, Interfaccia IActiveScriptProperty"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
Ottiene la proprietà specificata dal parametro.  
  
## Sintassi  
  
```  
HRESULT GetProperty(  
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
 Il valore della proprietà da ottenere.  
  
 `pvarIndex`  
 Non utilizzato.  
  
 `pvarValue`  
 Valore della proprietà.  
  
 I valori consentiti per `dwProperty` sono descritti nella tabella seguente.  
  
|Costante|Valore|Significato|  
|--------------|------------|-----------------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|Induce il motore di script per sta in modalità Integer anziché la modalità a virgola mobile.|  
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
 L'host può utilizzare la proprietà di SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION per notificare a un motore di gestione di script che nessun altro modulo di gestione di script esiste per consentire all'oggetto globale.  Ad esempio, Internet Explorer può notificare al motore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che la pagina sottoposta a rendering contiene solo gli script [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Pertanto, solo il motore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] può aggiungere nuove proprietà nella finestra globale dell'oggetto e non esiste motore di scripting edition Visual Basic \(VBScript\) per eseguire la stessa operazione.  Il motore può ignorare questo flag o può utilizzarlo per ottimizzare la gestione dei nuovi membri aggiunti all'oggetto globale.  
  
 L'host può utilizzare la proprietà di SCRIPTPROP\_INVOKEVERSIONING per selezionare l'insieme di funzionalità di linguaggio per supportare quando il motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] viene avviato.  Se questa proprietà è impostata su 1 \(SCRIPTLANGUAGEVERSION\_5\_7\), le funzionalità del linguaggio disponibili sono uguali ad esempio quelli presenti nella versione 5,7 del motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Se è impostato su 2 \(SCRIPTLANGUAGEVERSION\_5\_8\), le funzionalità del linguaggio disponibili sono quelle presenti nella versione 5,7 oltre alle funzionalità aggiunte nella versione 5,8.  Per impostazione predefinita, questa proprietà è impostata su 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\), che equivale alla funzionalità del linguaggio impostata che è presente nella versione 5,7, a meno che l'host supporta un comportamento predefinito diverso.  Ad esempio, Internet Explorer 8 selezionare le funzionalità del linguaggio [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] di supporto nel motore di scripting [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] versione 5,8 per impostazione predefinita quando la modalità di documento per Internet Explorer 8 è "modalità di standard Internet Explorer 8".  
  
## Vedere anche  
 [Definizione di compatibilità di documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md)