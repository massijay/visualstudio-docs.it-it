---
title: "Interfaccia IActiveScriptSiteDebug Interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptSiteDebug"
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IActiveScriptSiteDebug Interface
Gli SmartHost implementano l'interfaccia `IActiveScriptSiteDebug` per eseguire la gestione di documenti e per partecipare al debug.  L'oggetto `IActiveScriptSite` in genere fornisce un'implementazione dell'interfaccia `IActiveScriptSiteDebug`.  Se questa operazione, chiamare il metodo `IActiveScriptSite::QueryInterface` per ottenere l'interfaccia `IActiveScriptSiteDebug`.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IActiveScriptSiteDebug` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Utilizzato dal motore di linguaggio delegare `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Restituisce l'oggetto applicazione di debug associato al sito dello script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Ottiene il nodo dell'applicazione in cui i documenti di script da aggiungere.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Consente a uno SmartHost determinare come gestire gli errori di runtime.|