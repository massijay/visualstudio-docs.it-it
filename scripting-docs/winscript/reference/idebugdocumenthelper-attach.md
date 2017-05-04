---
title: "IDebugDocumentHelper::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Attach"
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Attach
Aggiunge questo documento all'albero del documento.  
  
## Sintassi  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### Parametri  
 `pddhParent`  
 \[in\] la struttura ad albero del documento in cui questo documento verrà aggiunto.  Può essere Null.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo aggiunge questo documento all'albero del documento, utilizzando `pddhParent` come elemento padre.  Se `pddhParent` è `NULL`, questo documento verrà il documento di primo livello.  
  
## Vedere anche  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [Interfaccia IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)