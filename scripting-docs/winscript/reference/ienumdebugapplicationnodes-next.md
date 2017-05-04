---
title: "IEnumDebugApplicationNodes::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Next
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Next"
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Next
Recupera un numero specificato di segmenti nella sequenza di enumerazione.  
  
## Sintassi  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\] numero di segmenti da recuperare.  
  
 `pprddp`  
 \[out\] restituisce una matrice di interfacce `IDebugApplicationNode` che rappresenta i segmenti recuperati.  
  
 `pceltFetched`  
 \[out\] il numero effettivo dei segmenti recuperati dall'enumeratore.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo recupera un numero specificato di segmenti nella sequenza di enumerazione.  
  
## Vedere anche  
 [Interfaccia IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)