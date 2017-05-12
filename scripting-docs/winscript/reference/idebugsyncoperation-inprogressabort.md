---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
Annullare l'operazione in corso in un altro thread.  
  
## Sintassi  
  
```  
HRESULT InProgressAbort();  
```  
  
#### Parametri  
 Questo metodo non accetta parametri.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|l'operazione non può essere annullata.|  
|`E_ABORT`|Impossibile completare l'operazione.|  
  
## Note  
 L'amministratore processo di debug chiama questo metodo dal thread del debugger per annullare l'operazione in corso in un altro thread.  
  
 Se il metodo `InProgressAbort` non può completare l'operazione, restituisce `E_ABORT` il prima possibile.  Questo metodo può restituire `E_NOTIMPL` se l'operazione non può essere annullata.  
  
## Vedere anche  
 [Interfaccia IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)