---
title: "IScriptEntry::SetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetName"
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::SetName
Per le voci che rappresentano un solo oggetto \(ad esempio una funzione\), imposta il nome dell'oggetto.  
  
## Sintassi  
  
```  
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parametri  
 `psz`  
 \[in\] il nome del nuovo oggetto `IScriptEntry`.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)