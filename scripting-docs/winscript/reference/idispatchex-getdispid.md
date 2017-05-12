---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo GetDispID"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
Esegue il mapping di un singolo nome del membro al DISPID corrispondente, che può quindi essere utilizzato sulle chiamate successive a `IDispatchEx::InvokeEx`.  
  
## Sintassi  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### Parametri  
 `bstrName`  
 Passato il nome da associare.  
  
 `grfdex`  
 Determina le opzioni per ottenere l'identificatore di membri.  Può trattarsi di una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|fdexNameCaseSensitive|Le richieste tali la ricerca del nome vengono effettuate in un fatta distinzione tra maiuscole e minuscole.  Può essere ignorato da oggetto che non supporta la ricerca con distinzione tra maiuscole e minuscole.|  
|fdexNameEnsure|Richieste che il membro viene creata se non sono già disponibili.  Il nuovo membro deve essere creato con il valore `VT_EMPTY`.|  
|fdexNameImplicit|Indica che il chiamante cerca gli oggetti membro di un nome specifico quando l'oggetto di base non è specificato in modo esplicito.|  
|fdexNameCaseInsensitive|Le richieste tali la ricerca del nome vengono eseguite in modalità senza distinzione tra maiuscole e minuscole.  Può essere ignorato da oggetto che non supporta la ricerca senza distinzione tra maiuscole e minuscole.|  
  
 `pid`  
 Puntatore al percorso allocato dal chiamante riceva i risultati di DISPID.  Se si verifica un errore, `pid` contiene DISPID\_UNKNOWN.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|||  
|-|-|  
|`S_OK`|Riuscita.|  
|`E_OUTOFMEMORY`|Memoria insufficiente.|  
|`DISP_E_UNKNOWNNAME`|Il nome non era noto.|  
  
## Note  
 `GetDispID` può essere utilizzato al posto `GetIDsOfNames` per ottenere il DISPID per un membro specificato.  
  
 Poiché `IDispatchEx` consente l'aggiunta e l'eliminazione dei membri, l'insieme dei dispid non rimane costante per la durata di un oggetto.  
  
 Il parametro inutilizzato `riid` in `IDispatch::GetIDsOfNames` è stato rimosso.  
  
## Esempio  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)