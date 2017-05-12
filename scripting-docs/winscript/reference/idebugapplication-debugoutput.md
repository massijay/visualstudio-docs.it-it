---
title: "IDebugApplication::DebugOutput | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.DebugOutput
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::DebugOutput"
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::DebugOutput
Determina la stringa specificata venga visualizzato nell'ambiente di sviluppo integrato \(IDE\) del debugger.  
  
## Sintassi  
  
```  
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### Parametri  
 `pstr`  
 \[in\] stringa da visualizzare nel debugger.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo consente un motore di linguaggio il supporto di output di debug specifiche della lingua di implementazione.  La stringa in genere nella finestra di output del debugger.  
  
 Questo metodo fa `IApplicationDebugger::onDebugOutput` venga chiamato.  
  
## Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)