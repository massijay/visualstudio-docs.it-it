---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
Aggiunge il nome di un elemento a livello di radice allo spazio dei nomi degli script del motore di creazione.  *Di un elemento a livello di radice* è un oggetto che può contenere le proprietà e i metodi e che può contenere anche origine eventi.  
  
## Sintassi  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### Parametri  
 `pszName`  
 \[in\] il nome dell'elemento come visualizzato lo script.  Il nome deve essere univoco e persistente.  
  
 `dwFlags`  
 \[in\] i flag associati all'elemento denominato.  Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script.  Ciò consente l'accesso a proprietà, metodi ed eventi dell'elemento.<br /><br /> Per convenzione, le proprietà dell'elemento comprendono i membri figlio dell'elemento.  Di conseguenza, tutte le proprietà dell'oggetto figlio e metodi \(e i relativi membri figlio, in modo ricorsivo\) sono accessibili.|  
|SCRIPTITEM\_ISSOURCE|0x00000004|Indica gli eventi di origine dell'elemento che lo script può avere gestori eventi di script.|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|Indica che l'elemento è una raccolta di proprietà globali e metodi associati allo script.  I membri sono creati come variabili globali e metodi.|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|Indica che l'elemento deve essere salvato quando il motore di creazione di script viene salvato.|  
|SCRIPTITEM\_CODEONLY|0x00000200|Indica che l'elemento denominato rappresenta un oggetto solo codice e non ha un membro da creare.|  
|SCRIPTITEM\_NOCODE|0x00000400|Indica che l'elemento denominato è semplicemente un nome che è stato aggiunto e non ha nulla creare.|  
  
 `pdisp`  
 \[in\] `IDispatch` dell'oggetto `NamedItem` utilizzato per raccogliere i metodi, le proprietà, o l'origine evento.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)