---
title: "Metodo IActiveScriptSiteUIControl::GetUIBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Metodo IActiveScriptSiteUIControl::GetUIBehavior
Ottiene [Enumerazione SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md) che rappresenta la modalità di un controllo dell'interfaccia utente deve essere gestito.  
  
## Sintassi  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### Parametri  
 `UicItem`  
 Tipo del controllo.  
  
 `pUicHandling`  
 La modalità il controllo deve essere gestita.