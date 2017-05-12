---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptSiteWindow"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
L'interfaccia viene implementata da host che supportano un'interfaccia utente nello stesso oggetto [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  Gli host che non supportano un'interfaccia utente, come server, non implementerebbero l'interfaccia `IActiveScriptSiteWindow`.  Il motore di scripting accede a questa interfaccia chiamando `QueryInterface` da `IActiveScriptSite`.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera l'handle della finestra che può essere utilizzato come proprietario di una finestra popup che il motore di scripting deve visualizzare.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Nell'host per abilitare o disabilitare la finestra principale e tutte le finestre di dialogo non modale.|  
  
## Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)