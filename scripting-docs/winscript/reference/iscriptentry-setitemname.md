---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
Imposta il nome che identifica un oggetto `IScriptEntry`.  
  
## Sintassi  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parametri  
 `psz`  
 \[in\] indirizzo di un buffer che contiene il nome.  Il nome utilizzato dall'host di identificare la voce.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Il metodo non è riuscita.|  
  
## Note  
 Per gli oggetti `IScriptEntry`, questo metodo restituisce `S_OK`.  
  
 Per gli oggetti `IScriptScriptlet` \(che derivano da `IScriptEntry`\), questo metodo restituisce `E_FAIL`.  Per gli oggetti `IScriptScriptlet`, il nome dell'elemento è impostato da [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) e non può essere modificato.  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)