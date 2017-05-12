---
title: "IRemoteDebugApplicationEx:SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:SetLocale
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:SetLocale"
ms.assetid: cd19f725-f4cd-453a-95e1-0bad676451da
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:SetLocale
Imposta il linguaggio per la localizzazione del debugger.  
  
## Sintassi  
  
```  
HRESULT SetLocale(  
   DWORD  dwLangID  
);  
```  
  
#### Parametri  
 `dwLangID`  
 \[in\] ID di linguaggio  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)