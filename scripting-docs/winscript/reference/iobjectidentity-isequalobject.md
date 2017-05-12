---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo IsEqualObject"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
Determina se un oggetto è uguale all'oggetto corrente.  
  
## Sintassi  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### Parametri  
 `punk`  
 \[in\] indirizzo dell'oggetto da confrontare all'oggetto corrente.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Gli oggetti sono uguali.|  
|`S_FALSE`|Gli oggetti non sono uguali.|  
  
## Note  
 Un'implementazione del metodo `IsEqualObject` deve restituire `S_OK` solo se gli oggetti sono identici.  
  
## Vedere anche  
 [Interfaccia IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)