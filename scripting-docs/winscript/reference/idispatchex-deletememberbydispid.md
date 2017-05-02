---
title: "IDispatchEx::DeleteMemberByDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo DeleteMemberByDispID"
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByDispID
Rimuove un membro da DISPID.  
  
## Sintassi  
  
```  
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### Parametri  
 `id`  
 Identificatore di membri.  Utilizzare `GetDispID` o `GetNextDispID` ottenere l'identificatore di invio.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|||  
|-|-|  
|`S_OK`|Riuscita.|  
|`S_FALSE`|Il membro esiste ma non può essere eliminato.|  
  
## Note  
 Se il membro viene eliminato, il DISPID deve rimanere valido per `GetNextDispID`.  
  
 Se un membro con il nome specificato viene eliminato e successivamente un membro con lo stesso nome viene ricreato, il DISPID deve corrispondere.  Se i nomi dei membri che differiscono solo in caso di "stesso" è con dipendente.\)  
  
## Esempio  
  
```  
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)