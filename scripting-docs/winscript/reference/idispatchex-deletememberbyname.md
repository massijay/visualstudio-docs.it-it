---
title: "IDispatchEx::DeleteMemberByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.DeleteMemberByName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo DeleteMemberByName"
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::DeleteMemberByName
Rimuove un membro per nome.  
  
## Sintassi  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### Parametri  
 `bstrName`  
 Nome del membro da eliminare.  
  
 `grfdex`  
 Determina se il nome del membro viene applicata la distinzione tra maiuscole e minuscole.  Ciò può essere uno dei seguenti valori:  
  
|Valore|Significato|  
|------------|-----------------|  
|fdexNameCaseSensitive|Le richieste tali la ricerca del nome vengono effettuate in un fatta distinzione tra maiuscole e minuscole.  Può essere ignorato da oggetto che non supporta la ricerca con distinzione tra maiuscole e minuscole.|  
|fdexNameCaseInsensitive|Le richieste tali la ricerca del nome vengono eseguite in modalità senza distinzione tra maiuscole e minuscole.  Può essere ignorato da oggetto che non supporta la ricerca senza distinzione tra maiuscole e minuscole.|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|||  
|-|-|  
|`S_OK`|Riuscita.|  
|`S_FALSE`|Il membro esiste ma non può essere eliminato.|  
  
## Note  
 Se il membro viene eliminato, il DISPID deve rimanere valido per `GetNextDispID`.  
  
 Se un membro con il nome specificato viene eliminato e successivamente un membro con lo stesso nome viene ricreato, il DISPID deve corrispondere.  Se i membri che differiscono solo in caso di "stesso" è con dipendente.\)  
  
## Esempio  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)