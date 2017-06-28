---
title: "Preparazione al debug: tipi di progetto Visual C++ | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "compilazioni di debug, impostazioni di progetto"
  - "debug [C++]"
  - "modelli di progetto, debug"
  - "progetti Visual C++, debug"
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Preparazione al debug: tipi di progetto Visual C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione viene descritto come eseguire il debug dei tipi di progetto di base creati mediante i modelli di progetto [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
 Si tenga presente che i tipi di progetto che consentono di creare DLL come output vengono tutti descritti in [Debug di progetti di DLL](../debugger/debugging-dll-projects.md) perché presentano caratteristiche comuni.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 [Impostazioni consigliate delle proprietà](#BKMK_Recommended_Property_Settings)  
  
 [Progetti Win32](#BKMK_Win32_Projects)  
  
-   [Per eseguire il debug di un'applicazione Win32 in C o C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Per impostare manualmente una configurazione di debug](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Applicazioni Windows Form (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Impostazioni consigliate delle proprietà  
 Determinate proprietà devono essere impostate nello stesso modo per tutti gli scenari di debug non gestito.  Nelle tabelle riportate di seguito sono indicate le impostazioni consigliate delle proprietà.  Le impostazioni non specificate in queste tabelle possono variare in base al tipo di progetto non gestito.  Per ulteriori informazioni, vedere [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### Proprietà di configurazione &#124; C\/C\+\+ &#124; nodo Ottimizzazione  
  
|Nome proprietà|Impostazione|  
|--------------------|------------------|  
|**Ottimizzazione**|Impostare su **Disabilitato \(\/0d\).** L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente.  Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra **Disassembly** è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nelle finestre del codice sorgente.  È possibile che altre funzionalità, ad esempio il debug passo a passo, non funzionino come previsto.|  
  
### Proprietà di configurazione &#124; Linker &#124; nodo Debug  
  
|Nome proprietà|Impostazione|  
|--------------------|------------------|  
|**Genera informazioni di debug**|Si consiglia di impostare questa opzione sempre su **Sì \(\/DEBUG\)** per creare i simboli di debug e i file necessari per il debug.  Quando l'applicazione passa alla fase di produzione, è possibile disattivare questa opzione.|  
  
 [In questo argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Progetti Win32  
 Le applicazioni Win32 sono programmi Windows tradizionali scritti in C o C\+\+.  Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è una procedura molto semplice.  
  
 Le applicazioni Win32 includono applicazioni MFC e progetti ATL.  Utilizzano API Windows e possono utilizzare MFC o ATL, ma non Common Language Runtime \(CLR\).  Possono, tuttavia, chiamare codice gestito che utilizza CLR.  
  
 Nella procedura riportata di seguito viene descritto come eseguire il debug di un progetto Win32 dall'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per eseguire il debug di un'applicazione Win32 è anche possibile avviare l'applicazione all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e stabilire una connessione.  Per ulteriori informazioni, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Per eseguire il debug di un'applicazione Win32 in C o C\+\+  
  
1.  Aprire il progetto in Visual Studio.  
  
2.  Scegliere **Avvia** dal menu **Debug**.  
  
3.  Eseguire il debug utilizzando le tecniche descritte in [Nozioni di base sul debugger](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Per impostare manualmente una configurazione di debug  
  
1.  Scegliere **Pagine delle proprietà** dal menu **Visualizza**.  
  
2.  Se non è ancora aperto, fare clic sul nodo **Proprietà di configurazione** per espanderlo.  
  
3.  Selezionare **Generale** e impostare il valore della riga **Output** su **Debug**.  
  
4.  Espandere il nodo **C\/C\+\+** e selezionare **Generale**.  
  
     Nella riga **Debug** specificare il tipo di informazioni di debug che dovrà essere generato dal compilatore.  I valori tra cui è possibile scegliere includono **Database di programma \(\/Zi\)** e **Database di programma per Modifica e continuazione \(\/ZI\)**.  
  
5.  Selezionare **Ottimizzazione** e nella riga **Ottimizzazione** scegliere **Disabilitato \(\/0d\)** dall'elenco a discesa.  
  
     L'esecuzione del debug di codice ottimizzato è più complessa perché le istruzioni generate non corrispondono direttamente al codice sorgente.  Se si nota un bug presente solo nel codice ottimizzato del programma, è possibile attivare questa impostazione, tenendo però presente che il codice riportato nella finestra Disassembly è generato da codice sorgente ottimizzato che potrebbe non corrispondere a quanto visualizzato nelle finestre del codice sorgente.  È probabile che alcune funzionalità, ad esempio il debug passo a passo, non visualizzino i punti di interruzione e i punti di esecuzione in modo corretto.  
  
6.  Espandere il nodo **Linker** e selezionare **Debug**.  Nella prima riga di **Genera informazioni di debug** selezionare **Sì \(\/DEBUG\)** dall'elenco a discesa.  Utilizzare sempre questa impostazione durante il debug.  
  
 Per ulteriori informazioni, vedere[Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [In questo argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Applicazioni Windows Form \(.NET\)  
 Il modello **Applicazione Windows Forms \(.NET\)** consente di creare un'applicazione Windows Form in [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  Per ulteriori informazioni, vedere [How to: Create a Windows Application Project](http://msdn.microsoft.com/it-it/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è simile a quello delle applicazioni Windows Form gestite.  
  
 Quando si crea un progetto di Windows Form mediante il modello di progetto, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio.  Se necessario, è possibile modificare queste impostazioni nella finestra di dialogo **Pagine delle proprietà di \<nomeprogetto\>**.  Per ulteriori informazioni, vedere [Procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Per ulteriori informazioni, vedere [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Per eseguire il debug di un'applicazione Windows Form è anche possibile avviare l'applicazione all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e stabilire una connessione.  Per ulteriori informazioni, vedere [Connessione a uno o più programmi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [In questo argomento](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## Vedere anche  
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Connessione a uno o più programmi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configurazioni versioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/it-it/b2f93fed-c635-4705-8d0e-cf079a264efa)