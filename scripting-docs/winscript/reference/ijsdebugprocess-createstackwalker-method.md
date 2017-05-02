---
title: "Metodo IJsDebugProcess::CreateStackWalker | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugProcess::CreateStackWalker
Metodo factory del percorso di chiamate nello stack.  
  
## Sintassi  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### Parametri  
 `threadId`  
 \[in\] ID di thread.  
  
 `ppStackWalker`  
 \[out\] Nuovo oggetto del percorso chiamate dello stack.  
  
## Valore restituito  
  
## Note  
 Restituisce E\_JsDEBUG\_UNKNOWN\_THREAD se il thread non presenta codice JavaScript.  Questo metodo può essere chiamato solo all'interruzione del processo di destinazione.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)