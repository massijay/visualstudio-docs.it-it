---
title: "Interfaccia IActiveScriptErrorDebug110 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptErrorDebug110"
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Interfaccia IActiveScriptErrorDebug110
Aggiunge funzionalità al [Interfaccia IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md).  Questa interfaccia viene implementata dal motore JavaScript per determinare il motivo per cui si è verificato un evento BREAKREASON\_ERROR.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva.  Rilevata in activdbg100.h.  
  
## Metodi  
 L'interfaccia `IActiveScriptErrorDebug110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Restituisce il tipo di eccezione per un'eccezione generata.|