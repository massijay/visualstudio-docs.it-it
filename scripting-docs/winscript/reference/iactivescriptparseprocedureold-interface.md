---
title: "Interfaccia IActiveScriptParseProcedureOld | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParseProcedureOld
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Interfaccia IActiveScriptParseProcedureOld"
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IActiveScriptParseProcedureOld
Consente il testo del codice sorgente per le procedure vengano aggiunti allo script.  Per i linguaggi di script interpretati che non dispongono di un ambiente indipendente di creazione, come VBScript, questo fornisce un meccanismo alternativo \(diverso da `IActiveScriptParse` o `IPersist*`\) per aggiungere le routine di script allo spazio dei nomi.  
  
> [!NOTE]
>  Questa interfaccia è deprecata a favore dell'interfaccia `IActiveScriptParseProcedure`.  
  
## Metodi  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IActiveScriptParseProcedureOld` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|Analizzare il codice di creazione specificato e aggiunge la routine allo spazio dei nomi.|  
  
## Vedere anche  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)