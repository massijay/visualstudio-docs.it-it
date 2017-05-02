---
title: "IDispatchEx::GetNextDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNextDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo GetNextDispID"
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNextDispID
Enumera i membri dell'oggetto.  
  
## Sintassi  
  
```  
HRESULT GetNextDispID(  
   DWORD grfdex,  
   DISPID id,  
   DISPID *pid  
);  
```  
  
#### Parametri  
 `grfdex`  
 Determina il set di elementi deve essere enumerato.  Può trattarsi di una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|fdexEnumDefault|Richieste che l'oggetto enumera gli elementi predefiniti.  L'oggetto è consentito per enumerare qualsiasi set di elementi.|  
|fdexEnumAll|Richieste che l'oggetto enumera elementi.  L'oggetto è consentito per enumerare qualsiasi set di elementi.|  
  
 `id`  
 Identifica il membro corrente.  GetNextDispID recupera l'elemento nell'enumerazione dopo questa.  Utilizzare GetDispID o una chiamata precedente a GetNextDispID ottenere questo identificatore.  Utilizza il valore di DISPID\_STARTENUM per ottenere il primo identificatore del primo elemento.  
  
 `pid`  
 L'indirizzo di una variabile di SPECIFICARE che riceve l'identificatore dell'elemento successivo nell'enumerazione.  
  
 Se un membro viene eliminato da `DeleteMemberByName` o da `DeleteMemberByDispID`, le necessità `DISPID` di rimanere valido per `GetNextDispID`.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|||  
|-|-|  
|`S_OK`|Riuscita.|  
|`S_FALSE`|L'enumerazione viene eseguita.|  
  
## Esempio  
  
```  
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
      SysFreeString(bstrName);  
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](#lrfidispatchexgetnextdispid)   
 [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)   
 [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)