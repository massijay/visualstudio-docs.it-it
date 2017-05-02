---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
Restituisce una delle statistiche standard dello script.  
  
## Sintassi  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### Parametri  
 `stid`  
 \[in\] specifica che aggiuntivi da restituire.  Deve essere il valore:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|Restituisce il numero di istruzioni eseguite poiché lo script avviato o le statistiche è stata reimpostata.|  
  
 `pluHi`  
 \[out\] i bit di livello 32 di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 \[out\] i bit di almeno 32 di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati ai valori nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo restituisce una delle statistiche standard dello script.  
  
## Vedere anche  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)