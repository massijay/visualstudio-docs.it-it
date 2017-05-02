---
title: "Enumerazione SCRIPTUICITEM | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fbf01f1b-5d7f-4d92-8d10-3da65e352d93
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Enumerazione SCRIPTUICITEM
Rappresenta il tipo di elemento dell'interfaccia utente.  Utilizzato in [Metodo IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).  
  
## Sintassi  
  
```vb  
typedef enum tagSCRIPTUICITEM {   
    SCRIPTUICITEM_INPUTBOX = 1,   
    SCRIPTUICITEM_MSGBOX = 2,   
    } SCRIPTUICITEM;  
  
```  
  
## Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTUICITEM\_INPUTBOX|Un controllo di input.|  
|SCRIPTUICITEM\_MSGBOX|Una finestra di messaggio.|