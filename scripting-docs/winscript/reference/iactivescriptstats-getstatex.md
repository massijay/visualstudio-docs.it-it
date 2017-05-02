---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
Restituisce una statistica personalizzata dello script.  
  
## Sintassi  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### Parametri  
 `guid`  
 \[in\] specifica che aggiuntivi da restituire.  La semantica di cui la statistica corrisponde a un GUID sia completamente motore definita.  
  
 `pluHi`  
 \[out\] i bit di livello 32 di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 \[out\] i bit di almeno 32 di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## Note  
 Questo metodo consente un motore di gestione di script personalizzato alle statistiche di ritorno significative a un host personalizzato.  
  
> [!NOTE]
>  Metodo non attualmente implementato.  
  
## Vedere anche  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)