---
title: "Interfaccia IDebugDocumentHost | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugDocumentHost"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugDocumentHost
Espone la funzionalità di protezione specifica, come colorazione della sintassi, il debugger.  Il metodo `IDebugDocumentHelper::SetDebugDocumentHost` utilizza questa interfaccia come argomento.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugDocumentHost` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Restituisce un intervallo di caratteri che sono stati aggiunti tramite `IDebugDocumentHelper::AddDeferredText`, nel documento originale host.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Restituisce gli attributi di testo da un blocco di testo del documento.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Notifica all'host che un contesto del nuovo documento viene creato e consente all'host possibile restituire un oggetto che controlla il nuovo contesto.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Restituisce il percorso completo \(nome file incluso\) del file di origine del documento.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Restituisce il nome del documento, senza informazioni sul percorso.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Notifica all'host che il file di origine del documento è stato salvato e che i contenuti devono essere aggiornati.|