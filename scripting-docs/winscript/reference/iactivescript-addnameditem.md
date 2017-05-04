---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo AddNamedItem, Interfaccia IActiveScript"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
Aggiunge il nome di un elemento a livello di radice allo spazio dei nomi del motore di scripting.  Di un elemento a livello di radice è un oggetto con proprietà e metodi, un'origine eventi, o tutti e tre le.  
  
## Sintassi  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### Parametri  
 `pstrName`  
 \[in\] indirizzo di un buffer che contiene il nome dell'elemento come visualizzato lo script.  Il nome deve essere univoco e persistente.  
  
 `dwFlags`  
 \[in\] i flag associata a un elemento.  Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTITEM\_CODEONLY|Indica che l'elemento denominato rappresenta un oggetto solo codice e che l'host non ha `IUnknown` da associare a questo oggetto solo codice.  L'host ha solo un nome per questo oggetto.  In linguaggi orientati a oggetti come C\+\+, questo flag creerebbe la classe.  Non tutti i linguaggi supportano questo flag.|  
|SCRIPTITEM\_GLOBALMEMBERS|Indica che l'elemento è una raccolta di proprietà globali e metodi associati allo script.  In genere, un motore di scripting in cui viene ignorata il nome dell'oggetto \(oltre a scopo del cookie come per il metodo [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md), o per risolvere definizione esplicita\) ed espone i membri quali le variabili globali e metodi.  Consente all'host dalla raccolta \(funzioni di runtime e così via\) disponibile solo lo script.  Viene lasciato al motore di script per gestire i conflitti di nomi, ad esempio quando due elementi di SCRIPTITEM\_GLOBALMEMBERS dispongono di metodi con lo stesso nome\), sebbene un errore non deve essere restituito a causa di questa situazione.|  
|SCRIPTITEM\_ISPERSISTENT|Indica che l'elemento deve essere salvato quando il motore di scripting viene salvato.  Analogamente, impostare questo flag indica che una transizione di nuovo allo stato inizializzato deve mantenere il nome dell'elemento e le informazioni sul tipo \(il motore di scripting deve, tuttavia, rilasciare tutti i puntatori alle interfacce l'effettivo oggetto\).|  
|SCRIPTITEM\_ISSOURCE|Indica che l'elemento origina gli eventi che lo script può effettuare il sink.  Gli oggetti figlio \(proprietà dell'oggetto che rappresentano direttamente oggetti\) possono anche agli eventi allo script.  Ciò non è ricorsiva, ma fornisce un meccanismo utile per il caso più comune, ad esempio, di creare un contenitore e tutti i relativi controlli del membro.|  
|SCRIPTITEM\_ISVISIBLE|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script, che consente l'accesso a proprietà, metodi ed eventi dell'elemento.  Per convenzione le proprietà dell'elemento sono inclusi gli elementi figlio dell'elemento; pertanto, qualsiasi proprietà dell'oggetto figlio e metodi \(e i relativi elementi figlio, in modo ricorsivo saranno accessibili.|  
|SCRIPTITEM\_NOCODE|Indica che l'elemento è semplicemente un nome che è stato aggiunto allo spazio dei nomi di script e non deve essere considerato come un codice dell'elemento per il quale deve essere associato.  Ad esempio, senza il flag impostato, VBScript creerà un modulo separato per l'elemento denominato e C\+\+ può creare una classe wrapper separata per l'elemento denominato.|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)