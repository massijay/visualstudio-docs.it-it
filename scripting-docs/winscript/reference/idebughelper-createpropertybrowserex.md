---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
Restituisce un Visualizzatore proprietà che esegue il wrapping di un VARIANT e consente la conversione personalizzata dei valori VARIABILI o VARTYPE digitare le stringhe.  
  
## Sintassi  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### Parametri  
 `pvar`  
 \[in\] variante della radice da visualizzare.  
  
 `bstrName`  
 \[in\] nome per fornire la radice.  
  
 `pdat`  
 \[in\] thread in cui per richiedere le proprietà.  Se questo parametro è NULL, alcun marshalling viene eseguito.  
  
 `pdf`  
 \[in\] oggetto che fornisce formattazione personalizzata per le variabili.  
  
 `ppdob`  
 \[out\] il Visualizzatore proprietà.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo restituisce un Visualizzatore proprietà che esegue il wrapping di un VARIANT e consente la conversione personalizzata dei valori VARIABILI o VARTYPE digitare le stringhe.  
  
## Vedere anche  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Interfaccia IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)