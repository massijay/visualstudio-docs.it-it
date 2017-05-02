---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
Recupera l'handle della finestra che può essere utilizzato come proprietario di una finestra popup che il motore di scripting deve visualizzare.  
  
## Sintassi  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### Parametri  
 `phwnd`  
 \[out\] indirizzo di una variabile che riceve un handle di finestra.  
  
## Valore restituito  
 Restituisce `S_OK` se l'operazione riesce, o `E_FAIL` se si è verificato un errore.  
  
## Note  
 Questo metodo è analogo al metodo `IOleWindow::GetWindow`.  
  
## Vedere anche  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)