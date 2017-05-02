---
title: "Interfaccia IScriptEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IScriptEntry"
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Interfaccia IScriptEntry
Un oggetto che implementa l'interfaccia `IScriptEntry` rappresenta un blocco di script o un oggetto funzione.  
  
 Oltre ai metodi ereditati da `IScriptNode`, l'interfaccia `IScriptEntry` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Restituisce il testo che corrisponde al corpo di un blocco di script, un blocco funzione, o di uno scriptlet `IScriptEntry`.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Restituisce il nome che identifica un oggetto `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Per le voci che rappresentano un solo oggetto \(ad esempio una funzione\), restituisce il nome dell'oggetto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Restituisce la posizione iniziale e la lunghezza di una voce.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Restituisce informazioni sui tipi per un oggetto funzione `IScriptEntry`.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Restituisce il testo corrispondente a un blocco di script `IScriptEntry`, o il codice sorgente contenuto in un gestore eventi `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Imposta il testo che è il corpo di un blocco di script `IScriptEntry` o di uno scriptlet `IScriptScriptlet`.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Imposta il nome che identifica un oggetto `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Per le voci che rappresentano un solo oggetto \(ad esempio una funzione\), imposta il nome dell'oggetto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Imposta le informazioni relative a un oggetto funzione `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Imposta il testo corrispondente a un blocco di script `IScriptEntry`, o il codice sorgente contenuto in un gestore eventi `IScriptScriptlet`.|  
  
## Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)