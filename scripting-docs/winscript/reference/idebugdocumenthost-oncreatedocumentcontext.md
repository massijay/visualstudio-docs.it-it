---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
Notifica all'host che un contesto del nuovo documento viene creato e consente all'host possibile restituire uno sconosciuto di controllo per il nuovo contesto.  
  
## Sintassi  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### Parametri  
 `ppunkOuter`  
 \[out\] un oggetto che controlla il nuovo contesto.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|l'host non fornisce un oggetto di controllo.|  
  
## Note  
 Questo metodo consente all'host aggiungere la nuova funzionalità a helper\- forniva i contesti di documento.  Questo metodo può restituire **E\_NOTIMPL** o un oggetto esterno null, nel qual caso il chiamante è responsabile della creazione il contesto.  
  
## Vedere anche  
 [Interfaccia IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)