---
title: "Interfaccia IActiveScriptWinRTErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptWinRTErrorDebug"
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Interfaccia IActiveScriptWinRTErrorDebug
Implementato dal motore JavaScript per fornire informazioni sull'errore estese di Windows Runtime da un evento [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md).  È possibile eseguire un QueryInterface di ottenerle da un oggetto [IActiveScriptError](../../winscript/reference/iactivescripterror.md).  
  
> [!IMPORTANT]
>  L'interfaccia viene implementata da PDM v11.0 e maggiore.  Trovato in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IActiveScriptWinRTErrorDebug` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Restituisce il PROCESSO di funzionalità di Windows errore di Runtime, se disponibile.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Restituisce la stringa di riferimento di errore limitata Windows Runtime, se disponibile.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Restituisce la stringa di errore limitata Windows Runtime, se disponibile.|