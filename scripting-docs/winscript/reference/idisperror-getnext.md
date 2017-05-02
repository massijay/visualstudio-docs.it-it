---
title: "IDispError::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetNext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetNext"
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetNext
Recupera l'oggetto successivo `IDispError`.  
  
## Sintassi  
  
```  
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### Parametri  
 `ppde`  
 \[out\] specifica l'oggetto successivo `IDispError`.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo recupera l'oggetto successivo `IDispError`.  Se questo è l'ultimo oggetto `IDispError`, questo metodo restituisce NULL.  
  
> [!NOTE]
>  Il metodo non è implementato.  
  
## Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)