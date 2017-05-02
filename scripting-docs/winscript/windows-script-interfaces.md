---
title: "Interfacce Windows Script | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Interfacce Windows Script
Le interfacce di Microsoft Windows Script consentono a un'applicazione per aggiungere script e l'automazione OLE.  Gli host di script che si basano sullo script di Windows possono utilizzare i moduli di gestione di script da più database di origine e da fornitori per gestire gli script tra i componenti.  L'implementazione dello stesso linguaggio di script, la sintassi, il formato persistente, modello di esecuzione e così via viene lasciato al fornitore dello script.  
  
 La documentazione di Windows è suddivisa nelle sezioni seguenti:  
  
 [Windows Script Host](../winscript/windows-script-hosts.md)  
  
 [Motori di script Windows](../winscript/windows-script-engines.md)  
  
 [Panoramica di debug script ActiveX](../winscript/active-script-debugging-overview.md)  
  
 [Panoramica di profilatura di script ActiveX](../winscript/active-script-profiling-overview.md)  
  
 [Riferimenti interfacce Windows Script](../winscript/reference/windows-script-interfaces-reference.md)  
  
## Sfondo di Windows  
 Le interfacce di finestre sono suddivisi in due categorie: Host di finestre e il motore di script di Windows.  Un host crea un motore di scripting e le chiamate sul modulo per eseguire script.  Esempi di host di finestre sono:  
  
-   Microsoft Internet Explorer  
  
-   Strumenti di creazione Internet  
  
-   Shell  
  
 I moduli di gestione di script di Windows possono essere compilati per qualsiasi linguaggio o ambiente di runtime, tra cui:  
  
-   Scripting edition Microsoft Visual Basic \(VBScript\)  
  
-   Perl  
  
-   Lisp  
  
 Per semplificare l'implementazione dell'host flessibile possibile, un wrapper di automazione OLE per lo script di Windows è fornito.  Tuttavia, un host che utilizza questo oggetto wrapper per creare un'istanza del motore di scripting non dispone del livello di controllo sullo spazio dei nomi in fase di esecuzione, il modello di persistenza, e così via, che se utilizzare direttamente lo script di Windows.  
  
 La progettazione dello script di Windows isola elementi di interfaccia necessari solo in un ambiente di progettazione in modo da host nonauthoring quali i browser e visualizzatori\) e i moduli di gestione di script \(ad esempio, VBScript\) possono essere mantenuti leggeri.  
  
## L'architettura di base di Windows  
 Nella figura seguente viene illustrata l'interazione tra Windows Script Host e un modulo di gestione di script di Windows.  
  
 I passaggi relativi all'interazione tra l'host e il motore l'elenco seguente sono riportati.  
  
1.  Creare un progetto.  L'host carica un progetto o un documento.  \(Questo passaggio non è determinato nello script di Windows, ma è incluso di seguito per completezza.\)  
  
2.  Creare il modulo di gestione di script di Windows.  L'host chiama `CoCreateInstance` per creare un modulo di gestione di script di Windows, specificando l'identificatore di classe \(CLSID\) del motore di scripting specifico da utilizzare.  Ad esempio, il browser HTML di Internet Explorer riceve identificatore di classe del motore di scripting con l'attributo di CLSID\= di tag HTML \<OBJECT\> .  
  
3.  Caricamento dello script.  Se il contenuto dello script sono stati salvati in modo permanente, l'host chiama il metodo di `IPersist*::Load` del modulo di gestione di script per inserirgli un'archiviazione, il flusso, o il contenitore delle proprietà dello script.  In caso contrario, l'host utilizza `IPersist*::InitNew` o il metodo di [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) per creare uno script null.  Un host che gestisce uno script come testo può utilizzare [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) per portare al motore di scripting il testo dello script, dopo avere chiamato `IActiveScriptParse::InitNew`.  
  
4.  Aggiungere denominato gli elementi.  Per ogni elemento denominato di primo livello quali pagine e di form\) incluso nello spazio dei nomi del motore di scripting, l'host chiama il metodo di [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) per creare una voce nello spazio dei nomi del modulo.  Questo passaggio non è necessaria per gli elementi denominati di primo livello fanno già parte dello stato persistente lo script caricato nel passaggio 3.  Un host non utilizza `IActiveScript::AddNamedItem` per aggiungere elementi denominati sottolivello \(come controlli in una pagina HTML\); invece, il motore ottiene indirettamente gli elementi di sottolivello gli elementi di livello principale tramite le interfacce di `ITypeInfo` e di `IDispatch` dell'host.  
  
5.  Eseguire lo script.  L'host induce il motore per avviare lo script impostando il flag di SCRIPTSTATE\_CONNECTED nel metodo di [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md).  Questa chiamata si esegue tutte le attività di costruzione del motore di scripting, inclusi un'associazione statica, agganciando fino a eventi \(vedere di seguito\) e il codice in esecuzione, in modo simile a una funzione basati su script di `main()`.  
  
6.  Ottenere le informazioni sull'elemento.  Ogni volta che il motore di gestione di script necessario associare un simbolo con un elemento di primo livello, chiama il metodo di [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md), che restituisce informazioni sull'elemento specificato.  
  
7.  Associare eventi.  Prima di iniziare effettivo di script, il motore di scripting si connette agli eventi di tutti gli oggetti rilevanti mediante l'interfaccia di `IConnectionPoint`.  
  
8.  Richiamare le proprietà e i metodi.  Mentre lo script, il motore di scripting esegue i riferimenti ai metodi e le proprietà degli oggetti denominati in `IDispatch::Invoke` o altri meccanismi di associazione OLE standard.  
  
## Termini dello script di Windows  
 Questo elenco contiene le definizioni dei termini correlati scripting\- utilizzati in questo documento.  
  
|Termine|Definizione|  
|-------------|-----------------|  
|Oggetto di codice|Un'istanza creata nel motore di scripting associato a un elemento denominato, ad esempio il modulo di un form in Visual Basic, o la classe c\+\+ associata a un elemento denominato.  Preferibilmente, questo è un oggetto di \(COM\) Component Object Model\) OLE all'automazione OLE supportate nell'host o un'altra entità dello script non possono modificare l'oggetto di codice.|  
|Elemento denominato|Un oggetto COM OLE \(possibilmente uno che supporta automazione OLE\) che l'host ha interessante allo script.  Gli esempi includono la pagina HTML e il browser in un Web browser e il documento e le finestre di dialogo di Microsoft Word.|  
|Script|I dati che costituiscono il programma che il motore di scripting esegue.  Uno script può essere tutti i dati eseguibili contigui, incluse le parti di testo, blocchi di `pcode`, o addirittura di codici eseguibili a specifici di byte.  Un host di caricare uno script nel motore di scripting con una delle interfacce di `IPersist*` o l'interfaccia di [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
|Motore di scripting|L'oggetto OLE che elabora gli script.  Un motore di scripting implementa le interfacce di [IActiveScriptParse](../winscript/reference/iactivescriptparse.md), facoltativamente, e di [IActiveScript](../winscript/reference/iactivescript.md).|  
|Host di script|L'applicazione o il programma che possiedono il modulo di gestione di script di Windows.  L'host implementa le interfacce di [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md), facoltativamente, e di [IActiveScriptSite](../winscript/reference/iactivescriptsite.md).|  
|Scriptlet|Una parte di script che viene associato a un oggetto tramite l'interfaccia di [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).  La raccolta di aggregazione di scriptlets è lo script.|  
|Linguaggio di script|Il linguaggio in cui uno script viene scritto \(VBScript, ad esempio\) e la semantica del linguaggio.|  
  
## Vedere anche  
 [Windows Script Interfaces](../winscript/windows-script-interfaces.md)