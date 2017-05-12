---
title: "IActiveScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScript"
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript
Fornisce i metodi necessari per inizializzare il motore di scripting.  Il motore di scripting deve implementare l'interfaccia `IActiveScript`.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Notifica al motore di scripting del sito [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) fornito dall'host.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Recupera l'oggetto del sito associato al modulo di gestione di script di windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Posizionare il modulo di gestione di scripting in stato specificato.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Recupera lo stato corrente del motore di scripting.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Induce il motore di script per annullare qualsiasi script attualmente caricato, per evitare perdite il relativo stato e rilasciare eventuali puntatori a interfaccia che deve altri oggetti, pertanto immettendo in uno stato chiuso.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Aggiunge il nome di un elemento a livello di radice allo spazio dei nomi del motore di scripting.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Aggiunge una libreria dei tipi nello spazio dei nomi per lo script.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Recupera l'interfaccia `IDispatch` per lo script.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Recupera un identificatore scripting\-motore\- definito per il thread attualmente in esecuzione.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Recupera un identificatore scripting\-motore\- definito per il thread associato al thread specificato Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Recupera lo stato corrente di un thread dello script.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Interrompere l'esecuzione di un thread in esecuzione dello script.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Duplica il motore di scripting corrente \(meno qualsiasi stato corrente di esecuzione, restituendo un motore di script caricato che non dispone di sito nel thread corrente.|  
  
## Vedere anche  
 [Riferimenti interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)