---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
Attende uno degli handle specificate da segnalare mentre nelle chiamate cross\-thread da inserire al thread.  Questo metodo deve essere chiamato dal thread del debugger.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) implementato da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Sintassi  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### Parametri  
 `handleCount`  
 Il numero di handle di attesa.  
  
 `pHandles`  
 Il set di handle di attesa.  
  
 `pIndex`  
 Quando il valore di HRESULT S\_OK, è l'indice in `pHandles` per gli handle che è stato segnalato.  
  
## Vedere anche  
 [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)