---
title: "IScriptEntry::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetName"
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::GetName
Per le voci che rappresentano un solo oggetto \(ad esempio una funzione\), restituisce il nome dell'oggetto.  
  
## Sintassi  
  
```  
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### Parametri  
 `pbstr`  
 \[out\] il nome dell'oggetto rappresentato dal blocco di script `IScriptEntry`.  Se un elemento non rappresenta un singolo oggetto, viene restituito NULL.  
  
 Le voci figlio rappresentano un singolo oggetto funzione.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)