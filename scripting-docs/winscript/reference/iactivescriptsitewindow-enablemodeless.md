---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
Nell'host per abilitare o disabilitare la finestra principale e tutte le finestre di dialogo non modale.  
  
## Sintassi  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### Parametri  
 `fEnable`  
 \[in\] diminuisca che, se `TRUE`, consente la finestra principale e le finestre di dialogo non modali o, se `FALSE`, le disabilitato.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_FAIL`se si è verificato un errore.  
  
## Note  
 Questo metodo è identico al metodo `IOleInPlaceFrame::EnableModeless`.  
  
 Le chiamate al metodo possono essere annidate.  
  
## Vedere anche  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)