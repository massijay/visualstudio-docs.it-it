---
title: "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp"
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Questo metodo crea congiuntamente la classe i cui ID passato in con `rclsid` utilizzando `dwClsContext`.  È simile al funzionamento [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) la modalità, ad eccezione del fatto che nel caso `CreateObjectWithSiteAtWebApp` l'oggetto viene creato in modo asincrono sul thread UI dell'applicazione web.  L'oggetto specificato da ID della classe deve implementare [Interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).  Dopo che l'oggetto è stato creato, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) viene chiamato con un riferimento all'applicazione di debug di PDM e il parametro `hPassToObject` `CreateObjectWithSiteAtWebApp`.  È possibile utilizzare questo metodo per trasformarti l'handle alle unnamed pipe di cui è stato copiato tramite [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
>  [Interfaccia IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) implementato da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Sintassi  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(  
        [in] REFCLSID rclsid,   
        [in] DWORD dwClsContext,   
        [in] REFIID riid,   
        [in] DWORD_PTR hPassToObject  
        );  
  
```  
  
#### Parametri  
 `rclsid`  
 L'id della classe da creare.  
  
 `dwClsContext`  
 Il contesto in cui il codice funzionerà.  In molti casi è CLSCTX\_INPROC\_SERVER.  
  
 `riid`  
 Non utilizzato.  
  
 `hPassToObject`  
 Un valore che verrà passato una volta all'oggetto viene creato sul thread UI, se l'oggetto implementa [Interfaccia IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).