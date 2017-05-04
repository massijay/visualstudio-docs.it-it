---
title: "IScriptEntry::GetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetItemName"
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::GetItemName
Restituisce il nome che identifica un oggetto `IScriptEntry`.  
  
## Sintassi  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### Parametri  
 `pbstr`  
 \[out\] indirizzo di un buffer che contiene il nome.  Il nome utilizzato dall'host di identificare la voce.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Per `IScriptScriptlet` oggetti, impostare il nome dell'elemento utilizzando [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md).  Per altre interfacce, impostare il nome dell'elemento utilizzando [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)