---
title: "IDispError::QueryErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.QueryErrorInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::QueryErrorInfo"
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::QueryErrorInfo
Recupera un determinato tipo di informazioni sugli errori.  
  
## Sintassi  
  
```  
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### Parametri  
 `guidErrorType`  
 \[in\] GUID che specifica il tipo di errore.  
  
 `ppde`  
 \[out\] specifica l'oggetto di IDispError.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Il metodo `QueryErrorInfo` recupera un determinato tipo di informazioni sugli errori.  
  
> [!NOTE]
>  Il metodo non è implementato.  
  
## Vedere anche  
 [Interfaccia IDispError](../../winscript/reference/idisperror-interface.md)