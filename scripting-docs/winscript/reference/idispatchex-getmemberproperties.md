---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo GetMemberProperties"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
Recupera le proprietà di un membro.  
  
## Sintassi  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### Parametri  
 `id`  
 Identifica il membro.  Utilizzare `GetDispID` o `GetNextDispID` ottenere l'identificatore di invio.  
  
 `grfdexFetch`  
 Determina le proprietà da recuperare.  Può trattarsi di una combinazione dei valori elencati in `pgrfdex` e\/o una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|grfdexPropCanAll|Combina il fdexPropCanGet, il fdexPropCanPut, il fdexPropCanPutRef, il fdexPropCanCall, il fdexPropCanConstruct e i fdexPropCanSourceEvents.|  
|grfdexPropCannotAll|Combina il fdexPropCannotGet, il fdexPropCannotPut, il fdexPropCannotPutRef, il fdexPropCannotCall, il fdexPropCannotConstruct e i fdexPropCannotSourceEvents.|  
|grfdexPropExtraAll|FdexPropNoSideEffects e fdexPropDynamicType le associazioni.|  
|grfdexPropAll|Combina il grfdexPropCanAll, il grfdexPropCannotAll e il grfdexPropExtraAll.|  
  
 `pgrfdex`  
 Indirizzo `DWORD` che riceve le proprietà richieste.  Può trattarsi di una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|fdexPropCanGet|Il membro può essere ottenuto utilizzando DISPATCH\_PROPERTYGET.|  
|fdexPropCannotGet|Il membro non può essere ottenuto utilizzando DISPATCH\_PROPERTYGET.|  
|fdexPropCanPut|Il membro può essere impostata utilizzando DISPATCH\_PROPERTYPUT.|  
|fdexPropCannotPut|Il membro non può essere impostata utilizzando DISPATCH\_PROPERTYPUT.|  
|fdexPropCanPutRef|Il membro può essere impostata utilizzando DISPATCH\_PROPERTYPUTREF.|  
|fdexPropCannotPutRef|Il membro non può essere impostata utilizzando DISPATCH\_PROPERTYPUTREF.|  
|fdexPropNoSideEffects|Il membro non ha effetti collaterali.  Ad esempio, un debugger potrebbe in modo sicuro ottenere\/set\/chiamata al membro senza modificare lo stato dello script che viene eseguito il debug.|  
|fdexPropDynamicType|Il membro è dinamico e può cambiare durante la durata dell'oggetto.|  
|fdexPropCanCall|Il membro può essere chiamato come metodo utilizzando DISPATCH\_METHOD.|  
|fdexPropCannotCall|Il membro non può essere chiamato come metodo utilizzando DISPATCH\_METHOD.|  
|fdexPropCanConstruct|Il membro può essere chiamato come costruttore che utilizza DISPATCH\_CONSTRUCT.|  
|fdexPropCannotConstruct|Il membro non può essere chiamato come costruttore che utilizza DISPATCH\_CONSTRUCT.|  
|fdexPropCanSourceEvents|Il membro può generare eventi.|  
|fdexPropCannotSourceEvents|Il membro non può generare eventi.|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|||  
|-|-|  
|`S_OK`|Riuscita.|  
|`DISP_E_UNKNOWNNAME`|Il nome non era noto.|  
  
## Esempio  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)