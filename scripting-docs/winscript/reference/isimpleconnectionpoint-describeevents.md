---
title: "ISimpleConnectionPoint::DescribeEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISimpleConnectionPoint.DescribeEvents
apilocation: pdm.dll
helpviewer_keywords: 
  - "ISimpleConnectionPoint::DescribeEvents"
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint::DescribeEvents
Restituisce il DISPID e il nome di ogni evento in un intervallo specificato degli eventi.  
  
## Sintassi  
  
```  
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### Parametri  
 `iEvent`  
 \[in\] indice del primo evento da recuperare.  
  
 `cEvents`  
 \[in\] numero di eventi da recuperare.  
  
 `prgid`  
 \[out\] matrice di valori di evento DISPID.  
  
 `prgbstr`  
 \[out\] matrice dei nomi degli eventi.  
  
 `pcEventsFetched`  
 \[out\] il numero effettivo di evento recuperati.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`S_FALSE`|Più eventi sono stati richiesti disponibile.  Gli eventi non sono rappresentati con DISPID\_NULL e un BSTR null.|  
|`E_INVALIDARG`|Nessun elemento può essere recuperato.|  
  
## Note  
 Questo metodo restituisce il DISPID e il nome di ogni evento in un intervallo specificato degli eventi.  
  
## Vedere anche  
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)