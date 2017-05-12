---
title: "Interfaccia IActiveScriptStats | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptStats"
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IActiveScriptStats
Consente a un host eseguire una query sulle statistiche di uno script.  L'host può utilizzare queste informazioni per stabilire se lo script è utilizzato troppo tempo per essere completata.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IActiveScriptStats` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Restituisce una delle statistiche standard dello script.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Restituisce una statistica personalizzata dello script.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Reimposta le statistiche per questo script.|