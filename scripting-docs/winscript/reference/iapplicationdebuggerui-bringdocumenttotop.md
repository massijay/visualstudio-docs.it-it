---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
Porta la finestra che contiene il documento specificato di debug all'interfaccia utente del debugger.  
  
## Sintassi  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### Parametri  
 `pddt`  
 \[in\] eseguire il debug del documento per portare all'interfaccia utente del debugger.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_INVALIDARG`|Il documento non è noto.|  
  
## Note  
 Questo metodo porta la finestra che contiene il documento specificato di debug all'interfaccia utente del debugger.  
  
## Vedere anche  
 [Interfaccia IApplicationDebuggerUI](../../winscript/reference/iapplicationdebuggerui-interface.md)