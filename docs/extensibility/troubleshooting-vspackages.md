---
title: Risoluzione dei problemi di VSPackage | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 933b0177e3287717b2cfb900996b947db7034ee5
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-vspackages"></a>Risoluzione dei problemi di VSPackage
Di seguito sono problemi comuni che potrebbero aver con il pacchetto Visual Studio e suggerimenti per risolvere i problemi.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Per risolvere un package VS che impedisce l'avvio di Visual Studio  
  
-   Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria.  
  
     Per avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modalità provvisoria, un prompt dei comandi, digitare **devenv.exe /safemode**.  
  
     Durante questo processo non vengono caricati VSPackage tranne il package VS che sono inclusi con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Per risolvere un package VS che non viene caricato  
  
1.  Assicurarsi che si sta utilizzando la radice del Registro di sistema in cui è registrato il package VS da eseguire, in genere la radice del Registro di sistema sperimentale.  
  
     Per ulteriori informazioni, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
2.  Se il package VS è destinato per l'esecuzione nella radice del Registro di sistema sperimentale, assicurarsi di eseguire la versione sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Per eseguire la versione sperimentale, digitare quanto segue nella finestra di comando: **devenv /rootsuffix exp**.  
  
3.  Controllare le voci del Registro di sistema di VSPackage.  
  
     Per ulteriori informazioni, vedere [registrazione VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) e [gestione package VS](../extensibility/managing-vspackages.md).  
  
4.  Aprire il **Output** finestra dell'istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che non riesce a caricare il VSPackage. Informazioni sui motivi per cui VSPackage non riesce a caricare potrebbero essere visualizzate in tale finestra.  
  
    > [!NOTE]
    >  Se si sta avviando versione sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE), controllare il **Output** finestra di entrambe le versioni.  
  
5.  Esaminare il registro attività.  
  
     Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Per ulteriori informazioni sulle eccezioni generate dall'IDE, fare clic su **eccezioni** sul **Debug** menu per abilitare le eccezioni. Nel **eccezioni** la finestra di dialogo selezionare i tipi di eccezioni su cui si desiderano ulteriori informazioni.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Per risolvere un package VS che non consente di registrare  
  
1.  Assicurarsi che l'assembly VSPackage risiede in un percorso attendibile. RegPkg Impossibile registrare l'assembly in una posizione non attendibile o parzialmente attendibile, ad esempio una condivisione di rete nella configurazione predefinita di sicurezza di .net. Anche se viene visualizzato un avviso ogni volta che un utente crea un progetto in una posizione non attendibile, la casella di controllo "non visualizzare più questo messaggio" può impedire l'avviso verifichi.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Per risolvere i problemi relativi a un comando che non è visibile o che genera un errore quando si sceglie un comando  
  
1.  Unire i comandi di menu nuovi o modificati e quelli già nell'IDE digitando quanto segue il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prompt dei comandi: **devenv /rootsuffix Exp /setup**.  
  
2.  Assicurarsi che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] UI.dll possibile cercare il pacchetto Visual Studio.  
  
    1.  Individuare il CLSID del VSPackage nella sezione pacchetti del Registro di sistema:  
  
         Studio HKLM\Software\Microsoft\Visual\\*\<versione >*\Packages  
  
    2.  Verificare che il percorso specificato per la sottochiave SatelliteDll sia corretto.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Per risolvere un package VS che si comporta in modo imprevisto  
  
1.  Impostare i punti di interruzione nel codice.  
  
     Punti di partenza ottimali per il debug sono il costruttore e il metodo di inizializzazione. È inoltre possibile impostare punti di interruzione nell'area di cui che si desidera valutare, ad esempio un comando di menu. Per abilitare i punti di interruzione, è necessario eseguire il debugger.  
  
    1.  Nel **progetto** menu, fare clic su **proprietà**.  
  
    2.  Nel **pagine delle proprietà** la finestra di dialogo, selezionare il **Debug** scheda.  
  
    3.  Nel **argomenti della riga di comando** , digitare il suffisso principale dell'ambiente di sviluppo che le destinazioni di VSPackage. Ad esempio, per selezionare la compilazione sperimentale, digitare: **RootSuffix Exp**.  
  
    4.  Nel **Debug** menu, fare clic su **Avvia debug** o premere F5.  
  
        > [!NOTE]
        >  Se si esegue il debug di un progetto, creare o caricare un'istanza esistente del progetto a questo punto.  
  
2.  Utilizzare il registro attività.  
  
     Traccia VSPackage comportamento scrivendo informazioni nel log di attività in punti chiave. Questa tecnica è particolarmente utile quando si esegue un pacchetto in un ambiente di vendita al dettaglio. Per ulteriori informazioni, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Utilizzare i simboli pubblici.  
  
     Per migliorare la leggibilità durante il debug, è possibile collegare i simboli per il debugger.  
  
    1.  Dal **Strumenti/opzioni** menu, passare al **debug/simboli** la finestra di dialogo.  
  
    2.  Aggiungere questo **percorso del file (con estensione pdb) di simboli**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Per migliorare le prestazioni, specificare una cartella della cache di simboli, ad esempio:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Per risolvere un VSPackage mancante o una delle relative dipendenze  
  
1.  Per codice gestito, assicurarsi che i percorsi di riferimento siano corretti.  
  
    1.  Nel **progetto** menu, fare clic su **proprietà**.  
  
    2.  Selezionare il **riferimenti** nella scheda il **pagine delle proprietà** la finestra di dialogo e assicurarsi che tutti i percorsi siano corretti. In alternativa, è possibile utilizzare il **Visualizzatore oggetti** per cercare gli oggetti di riferimento.  
  
         Per codice gestito, è possibile utilizzare il [Fuslogvw.exe (Visualizzatore Log associazione Assembly)](http://msdn.microsoft.com/Library/e32fa443-0778-4cc3-bf36-5c8ea297d296) per visualizzare i dettagli di caricamenti di assembly non riuscita.  
  
2.  Per codice non gestito, individuare il CLSID del VSPackage nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nodo CLSID del Registro di sistema:  
  
     Studio HKLM\Software\Microsoft\Visual\\*\<versione >*\CLSID  
  
 Assicurarsi che la voce InprocServer32 è il percorso corretto della dll VSPackage.  
  
## <a name="see-also"></a>Vedere anche  
 [Package VS](../extensibility/internals/vspackages.md)
