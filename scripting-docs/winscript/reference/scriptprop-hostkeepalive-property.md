---
title: "Propriet&#224; SCRIPTPROP_HOSTKEEPALIVE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Propriet&#224; SCRIPTPROP_HOSTKEEPALIVE
Utilizzata per specificare se il motore di scripting deve essere mantenuto completamente funzionale se sono presenti riferimenti costanti.  
  
 Utilizzare [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) per impostare la proprietà su `true`.  Se questa proprietà è impostata su `true`, il motore di scripting viene tenuto completamente funzionale finché esiste almeno un riferimento costante o al motore di scripting stesso o un puntatore di `IDispatch` a un oggetto JavaScript creato tramite il motore di scripting.  Quando questa proprietà è impostata su `true`, non chiamarlo in modo esplicito chiudere o reimpostare il modulo di gestione di script tramite i metodi di [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) o di [IActiveScript::Close](../../winscript/reference/iactivescript-close.md).  La versione dell'ultimo riferimento a un oggetto script chiude il modulo di gestione di script in basso.  
  
## Sintassi  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## Requisiti  
 Questa proprietà viene visualizzato solo nella versione di activscp.idl installato con [!INCLUDE[win8](../../javascript/includes/win8-md.md)], con il 2707082 KB per Internet Explorer 8 in [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], o al 2722913 KB per Internet Explorer 9 in [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] o su [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].