---
title: "Metodo IJsDebugDataTarget::GetThreadContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::GetThreadContext
Recupera il contesto del thread specificato.  
  
## Sintassi  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### Parametri  
 `threadId`  
 \[in\] Thread in esecuzione nel processo di destinazione.  
  
 `contextFlags`  
 \[in\] Specifica i flag di contesto.  Ciò equivale al campo ContextFlags di CONTEXT \(per ulteriori informazioni, vedere winnt.h, cercare CONTEXT\_ALL\).  
  
 `contextSize`  
 \[in\] Dimensione del buffer specificata da pContext.  
  
 `pContext`  
 \[out\] Riceve la struttura del CONTEXT specifica della piattaforma nel buffer specificato da pContext.  
  
## Valore restituito  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)