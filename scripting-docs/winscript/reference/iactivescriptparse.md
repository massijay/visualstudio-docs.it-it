---
title: "IActiveScriptParse | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptParse"
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParse
Se il modulo di gestione di script di windows consente di scriptlets di codice di testo non elaborato da aggiungere allo script o consente il testo di espressione da valutare in fase di esecuzione, implementa l'interfaccia `IActiveScriptParse`.  Per i linguaggi di script interpretati che non dispongono di ambiente indipendente di creazione, come VBScript, questo fornisce un meccanismo alternativo \(diverso da `IPersist*`\) per immettere il codice di script del motore di scripting e allegare i frammenti di script ai vari eventi dell'oggetto.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Inizializza il motore di scripting.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Aggiunge uno scriptlet di codice allo script.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analizza lo scriptlet specificato di codice, aggiungendo le dichiarazioni dello spazio dei nomi e valutazione il codice in base alle proprie esigenze.|  
  
## Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)