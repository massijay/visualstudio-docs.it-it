---
title: "Interfaccia IActiveScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptErrorDebug"
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IActiveScriptErrorDebug
Vengono fornite informazioni sul contesto di documento per gli errori in fase di compilazione ed eccezioni di runtime.  Il metodo `IActiveScriptError::QueryInterface` supporta l'interfaccia `IActiveScriptErrorDebug`.  
  
 Oltre ai metodi ereditati da `IActiveScriptError`, l'interfaccia `IActiveScriptErrorDebug` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Fornisce contesto del documento per questo errore.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Fornisce lo stack frame in effetti degli errori di runtime.|