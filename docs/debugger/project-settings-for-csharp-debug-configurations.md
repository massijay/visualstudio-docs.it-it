---
title: "Impostazioni di progetto per le configurazioni di debug C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "compilazioni di debug, impostazioni di progetto"
  - "configurazioni di debug, C#"
  - "configurazioni di debug, J#"
  - "debug [C#], impostazioni debugger"
  - "debug [J#], impostazioni debugger"
  - "configurazioni di progetto, debug"
  - "progetto (impostazioni) [Visual Studio], configurazioni di debug"
  - "progetti [Visual Studio], configurazioni di debug"
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Impostazioni di progetto per le configurazioni di debug C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare le impostazioni di progetto per una configurazione di debug C\# nella finestra **Pagine delle proprietà**, come descritto in [Configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
> [!WARNING]
>  Questo argomento non si applica alle app di Windows Store.  Vedere [Avviare una sessione di debug \(VB, C\#, C\+\+ e XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Scheda Debug  
  
|**Impostazione**|**Descrizione**|  
|----------------------|---------------------|  
|**Configurazione**|Imposta la modalità per la compilazione dell'applicazione.  Le opzioni disponibili sono **Attiva \(Debug\)**, **Debug**, **Release**, **Tutte le configurazioni**.|  
|**Avvia azione**|Questo gruppo di controlli specifica l'azione che verrà eseguita quando si sceglie Avvia dal menu Debug.<br /><br /> -   **Avvia progetto** è l'azione predefinita e avvia il progetto di avvio per il debug.  Per ulteriori informazioni, vedere [Scelta del progetto di avvio](http://msdn.microsoft.com/it-it/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Avvia programma esterno** consente di avviare un programma che non fa parte di un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e di stabilire una connessione a tale programma.  Per ulteriori informazioni, vedere [Connessione a un programma in esecuzione](http://msdn.microsoft.com/it-it/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Avvia browser con URL** consente di eseguire il debug di un'applicazione Web.|  
|**Argomenti della riga di comando**|Specifica gli argomenti della riga di comando per il programma da sottoporre a debug.  Il nome del comando è il nome del programma specificato in Avvia programma esterno.  Se l'opzione Azione di avvio è impostata su Avvia URL, non è possibile specificare gli argomenti della riga di comando.|  
|**Directory di lavoro**|Specifica la cartella di lavoro del programma sottoposto a debug.  In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \\bin\\debug.|  
|**Usa computer remoto**|Il nome di un computer remoto nel quale l'applicazione verrà eseguita ai fini del debug oppure un [nome di server Msvsmon](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  Il percorso del file EXE sul computer remoto è specificato dalla proprietà Percorso output nella cartella Proprietà di configurazione, categoria Compila.  Il percorso deve essere una directory condivisibile del computer remoto.|  
|**Attiva debug codice non gestito**|Consente di eseguire il debug delle chiamate al codice Win32 nativo \(non gestito\) dall'applicazione gestita in uso.|  
|**Attiva debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Scheda Compila  
  
|Impostazione|Descrizione|  
|------------------|-----------------|  
|**Simboli di compilazione condizionale:**|Le costanti DEBUG e TRACE vengono definite in questa posizione.<br /><br /> Esse attivano la compilazione condizionale della [Classe Debug](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) e della [Classe Trace](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Quando sono definite, i metodi delle classi Debug e Trace generano l'output per la [finestra di output](../ide/reference/output-window.md).  In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.<br /><br /> -   Debug è generalmente definito nella versione di debug di un programma, mentre non lo è nella versione di rilascio.<br />-   Trace è generalmente definito in entrambe le versioni di debug e di rilascio.|  
|**Ottimizza codice**|Questa impostazione deve rimanere disattivata nella versione di debug, a meno che non venga rilevato un bug solo nel codice ottimizzato.  L'esecuzione del debug di un codice ottimizzato è più complessa poiché le istruzioni non corrispondono direttamente alle istruzioni presenti nelle finestre del codice sorgente.|  
|**Percorso output**|Generalmente impostato su bin\\Debug per l'esecuzione del debug.|  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)