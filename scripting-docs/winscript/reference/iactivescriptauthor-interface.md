---
title: "Interfaccia IActiveScriptAuthor | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptAuthor"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Interfaccia IActiveScriptAuthor
Rappresenta i servizi di creazione, incluso IntelliSense e raccolta di informazioni.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IActiveScriptAuthor` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Aggiunge il nome di un elemento a livello di radice allo spazio dei nomi degli script del motore di creazione.  *Di un elemento a livello di radice* è un oggetto che può contenere le proprietà e i metodi e che può contenere anche origine eventi.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Aggiunge uno scriptlet di codice come figlio dell'oggetto livello radice `IScriptNode`.  Nell'host, il nome completo di scriptlet può contenere solo due livelli.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Aggiunge una libreria dei tipi nello spazio dei nomi per lo script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Restituisce il set di caratteri di completamento di un contesto di completamento richiesto.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Restituisce lo scriptlet con gli attributi specificati.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Restituisce informazioni sul tipo e percorsi di ancoraggio di un carattere specificato in un blocco di codice.  Ciò fornisce informazioni per il membro IntelliSense, elenchi globali e i suggerimenti di parametro.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Restituisce informazioni in lingua inglese\).|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Restituisce la radice `IScriptNode` albero di script all'autore.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Restituisce gli attributi di testo di una scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Restituisce gli attributi di testo di un blocco di script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Restituisce un valore che indica se un carattere specificato deve eseguire il commit del completamento delle istruzioni dall'applicazione.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analizza il testo dello script, aggiungere testo al motore di creazione di script di creazione e di creare un oggetto `IScriptEntry` che corrisponde al blocco di script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Rimuove un oggetto `NamedItem` dallo spazio dei nomi del motore di creazione di script.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Rimuove una libreria dei tipi dello spazio dei nomi del motore di creazione di script.|  
  
## Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)