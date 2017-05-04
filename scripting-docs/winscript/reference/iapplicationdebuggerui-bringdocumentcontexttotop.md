---
title: "IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentContextToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentContextToTop"
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentContextToTop
Porta la finestra che contiene il contesto specificato del documento all'interfaccia utente del debugger e scorre la finestra al contesto.  
  
## Sintassi  
  
```  
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### Parametri  
 `pddc`  
 \[in\] documenti il contesto per portare all'interfaccia utente del debugger.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Il contesto specificato da `pddc` non è noto.|  
  
## Note  
 Questo metodo porta la finestra che contiene il contesto specificato del documento all'interfaccia utente del debugger e scorre la finestra al contesto.  
  
## Vedere anche  
 [Interfaccia IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)