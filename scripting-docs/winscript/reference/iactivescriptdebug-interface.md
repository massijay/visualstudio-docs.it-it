---
title: "Interfaccia IActiveScriptDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptDebug"
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IActiveScriptDebug
Implementato nel motore di script che supportano il debug.  In genere, un oggetto che implementa l'interfaccia `IActiveScriptDebug` implementa anche l'interfaccia `IActiveScript`.  In questo caso, chiamare il metodo `IActiveScript::QueryInterface` per ottenere l'interfaccia `IActiveScriptDebug`.  
  
 l'interfaccia `IActiveScriptDebug` fornisce i mezzi per:  
  
-   SmartHost per assumere la direzione di gestione dei documenti.  
  
-   Amministratore del processo di debug per sincronizzare debug dei moduli di gestione di script in.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IActiveScriptDebug` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Restituisce gli attributi di testo da un blocco arbitrario di testo dello script.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Restituisce gli attributi di testo per uno scriptlet arbitrario.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delegati a `IDebugDocumentContext::EnumCodeContexts`.|