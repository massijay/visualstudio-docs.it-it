---
title: "IActiveScriptParseProcedure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptParseProcedure"
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptParseProcedure
Se il modulo di gestione di script di windows consente il testo del codice sorgente per le procedure verrà aggiungere lo script, implementa l'interfaccia `IActiveScriptParseProcedure`.  Per i linguaggi di script interpretati che non dispongono di ambiente indipendente di creazione, come VBScript, questo fornisce un meccanismo alternativo \(diverso da `IActiveScriptParse` o `IPersist`\*\) per aggiungere le routine di script allo spazio dei nomi.  
  
## Metodi nell'ordine Vtable  
  
|||  
|-|-|  
|Metodo|Descrizione|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|Analizzare il codice di creazione specificato e aggiunge la routine allo spazio dei nomi.|  
  
## Vedere anche  
 [Interfacce Script ActiveX](../../winscript/reference/active-script-interfaces.md)