---
title: "Impostazioni di progetto per una configurazione di debug Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbProjectPropertiesDebug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "compilazioni di debug, impostazioni di progetto"
  - "configurazioni di debug, Visual Basic"
  - "debug [Visual Basic], impostazioni debugger"
  - "configurazioni di progetto, debug"
  - "progetto (impostazioni) [Visual Studio], configurazioni di debug"
  - "progetti [Visual Studio], configurazioni di debug"
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Impostazioni di progetto per una configurazione di debug Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare le impostazioni di progetto per una configurazione di debug [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nella finestra di dialogo **Pagine delle proprietà**, come descritto in [Procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
> [!WARNING]
>  Questo argomento non si applica alle app Windows Store.  Vedere [Avviare una sessione di debug \(VB, C\#, C\+\+ e XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### Scheda Debug  
  
|Impostazione|Descrizione|  
|------------------|-----------------|  
|**Configurazione**|Imposta la modalità per la compilazione dell'applicazione.  Le opzioni disponibili sono **Attiva \(Debug\)**, **Debug**, **Release**, **Tutte le configurazioni**.|  
|**Azione di avvio**|Questo gruppo di controlli specifica l'azione che verrà eseguita quando si sceglie Avvia dal menu Debug.<br /><br /> -   **Avvia progetto** è l'azione predefinita e avvia il progetto di avvio per il debug.  Per ulteriori informazioni, vedere [Procedura: impostare progetti di avvio](http://msdn.microsoft.com/it-it/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Avvia programma esterno** consente di avviare un programma che non fa parte di un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e di stabilire una connessione a tale programma.  Per ulteriori informazioni, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Avvia browser con URL** consente di eseguire il debug di un'applicazione Web.|  
|**Argomenti della riga di comando**|Specifica gli argomenti della riga di comando per il programma da sottoporre a debug.  Il nome del comando è il nome del programma specificato in Avvia programma esterno.  Se l'opzione Azione di avvio è impostata su Avvia URL, gli argomenti della riga di comando verranno ignorati.|  
|**Cartella di lavoro**|Specifica la cartella di lavoro del programma sottoposto a debug.  In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione.  La cartella di lavoro predefinita è \\bin\\Debug or \\bin\\Release, a seconda della configurazione corrente.|  
|**Usa computer remoto**|Quando la casella di controllo è selezionata, il debug remoto è attivato.  Nella casella di testo è possibile digitare il nome di un computer remoto nel quale l'applicazione verrà eseguita ai fini del debug oppure un [nome di server Msvsmon](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  Il percorso del file EXE sul computer remoto è specificato dalla proprietà Percorso output nella scheda Compila.  Il percorso deve essere una directory condivisibile del computer remoto.|  
|**Debug codice non gestito**|Consente di eseguire il debug delle chiamate al codice Win32 nativo \(non gestito\) dall'applicazione gestita in uso.  Ha lo stesso effetto della selezione di Misto per Tipo debugger in un progetto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].|  
|**Debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
  
### Scheda Compila \(scegliere il pulsante Opzioni di compilazione avanzate\)  
  
|Impostazione|Descrizione|  
|------------------|-----------------|  
|**Attiva ottimizzazioni**|Si consiglia di non selezionare questa opzione.  L'ottimizzazione rende più difficile il debug perché il codice effettivamente eseguito è diverso dal codice sorgente visualizzato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se il codice è ottimizzato, non caricare i simboli per impostazione predefinita quando si esegue il debug con Just My Code.|  
|**Genera informazioni di debug**|Questa impostazione, predefinita in entrambe le versioni di debug e di rilascio ed equivalente all'opzione del compilatore \/debug, determina la creazione delle informazioni di debug in fase di compilazione.  Il debugger utilizza tali informazioni per mostrare i nomi delle variabili e altri dati in un formato utile quando si esegue il debug.  Se il programma viene compilato senza specificarle, la funzionalità del debugger risulterà limitata.  Per ulteriori informazioni, vedere [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|**Definisci costante DEBUG**|La definizione di questo simbolo attiva la compilazione condizionale delle funzioni di output della [classe Debug](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx).  Quando è definito, i metodi della classe Debug generano l'output per la [finestra di output](../ide/reference/output-window.md).  In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.  Questo simbolo deve essere definito nella versione di debug e non nella versione di rilascio.  La relativa definizione in una versione di rilascio determina la creazione di codice non necessario che rallenta l'esecuzione del programma.|  
|**Definisci costante TRACE**|La definizione di questo simbolo attiva la compilazione condizionale delle funzioni di output della [classe Trace](https://msdn.microsoft.com/en-us/library/system.diagnostics.trace.aspx).  Quando è definito, i metodi della classe Trace generano l'output per la [finestra di output](../ide/reference/output-window.md).  In caso contrario, tali metodi non verranno compilati e non verrà generato alcun output.  Questo simbolo è definito per impostazione predefinita in entrambe le versioni di debug e di rilascio.|  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)