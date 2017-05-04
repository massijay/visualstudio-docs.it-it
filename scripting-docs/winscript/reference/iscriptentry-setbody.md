---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
Imposta il testo che è il corpo di un blocco di script `IScriptEntry` o di uno scriptlet `IScriptScriptlet`.  
  
## Sintassi  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### Parametri  
 `psz`  
 \[in\] per un blocco di script `IScriptEntry`, `psz` è il testo racchiuso tra i tag script.  
  
 Per un blocco funzione `IScriptEntry`, `psz` è il corpo della funzione.  
  
 Per un oggetto `IScriptScriptlet` \(che deriva da `IScriptEntry`\), `psz` è il testo dello script di scriptlet.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)