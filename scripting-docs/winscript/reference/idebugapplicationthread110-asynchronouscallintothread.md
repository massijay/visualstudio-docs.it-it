---
title: "IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IDebugApplicationThread110::AsynchronousCallIntoThread
Effettua una chiamata asincrona nel thread principale.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) implementato da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Sintassi  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### Parametri  
 `pptc`  
 L'oggetto [Interfaccia IDebugThreadCall](../../winscript/reference/idebugthreadcall-interface.md) la chiamata.  
  
 `dwParam1`  
 Il primo parametro della chiamata.  
  
 `dwParam1`  
 Il primo parametro della chiamata.  
  
 `dwParam2`  
 Il secondo parametro della chiamata.  
  
 `dwParam3`  
 Il terzo parametro della chiamata.  
  
## Vedere anche  
 [Interfaccia IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md)