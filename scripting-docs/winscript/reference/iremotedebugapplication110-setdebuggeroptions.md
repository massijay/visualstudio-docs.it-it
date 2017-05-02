---
title: "IRemoteDebugApplication110::SetDebuggerOptions | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IRemoteDebugApplication110::SetDebuggerOptions"
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplication110::SetDebuggerOptions
Chiamato per aggiornare le opzioni del debugger.  Questo metodo deve essere chiamato dopo [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md).  Di [IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) di metodo bloccando automaticamente alle opzioni predefinite.  l'impostazione predefinita di opzioni a 0 \(SDO\_NONE\).  
  
> [!IMPORTANT]
>  [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md) implementato da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Sintassi  
  
```cpp  
HRESULT SetDebuggerOptions(  
        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,  
        [in] enum SCRIPT_DEBUGGER_OPTIONS value  
    );  
  
```  
  
#### Parametri  
 `mask`  
 La maschera [Enumerazione SCRIPT\_DEBUGGER\_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md).  
  
 `value`  
 Valore [Enumerazione SCRIPT\_DEBUGGER\_OPTIONS](../../winscript/reference/script-debugger-options-enumeration.md).  
  
## Vedere anche  
 [Interfaccia IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)   
 [Interfaccia IRemoteDebugApplication110](../../winscript/reference/iremotedebugapplication110-interface.md)