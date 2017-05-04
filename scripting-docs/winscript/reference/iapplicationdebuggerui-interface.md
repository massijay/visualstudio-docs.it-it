---
title: "Interfaccia IApplicationDebuggerUI | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IApplicationDebuggerUI"
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IApplicationDebuggerUI
Implementato dall'ambiente di sviluppo integrato \(IDE\) del debugger \(oltre a `IApplicationDebugger`\) per fornire a un componente esterno maggiore controllo sull'interfaccia utente \(UI\) del debugger.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IApplicationDebuggerUI` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Porta la finestra che contiene il documento specificato di debug all'interfaccia utente del debugger.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Porta la finestra che contiene il contesto specificato del documento all'interfaccia utente del debugger e scorre la finestra al contesto.|