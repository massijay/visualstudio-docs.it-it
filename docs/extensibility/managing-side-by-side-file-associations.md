---
title: "La gestione delle associazioni di File Side-by-Side | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verbi, l'impostazione predefinita"
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# La gestione delle associazioni di File Side-by-Side
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se il package VS fornisce alle associazioni di file, è necessario decidere come gestire le installazioni contemporanee in cui una determinata versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamata per aprire un file.  I formati di file incompatibili costituiscono il problema.  
  
 Gli utenti richiedere una nuova versione del prodotto per essere compatibili con le versioni precedenti, in modo che i file esistenti possono essere caricati in una nuova versione senza alcuna perdita.  In teoria, il package VS sia possibile caricare e salvare i formati di file delle versioni precedenti.  Se non è true, è necessario fornire migliorare il formato di file alla nuova versione del package VS.  Il lato negativo a questo approccio è che il file aggiornato non può essere aperto nella versione precedente.  
  
 Per evitare questo problema, è possibile modificare le estensioni quando i formati di file sono incompatibili.  Ad esempio, la versione 1 del package VS possibile utilizzare l'estensione, .mypkg10 e la versione 2 potrebbe utilizzare l'estensione, .mypkg20.  Questa differenza identifica il package VS che apre un file specifico.  Se si aggiungono più recente Vspackage all'elenco dei programmi associati a un'estensione precedente, gli utenti possono fare clic con il pulsante destro del mouse sul file e scegliere per aprirlo in uno più recente VSPackage.  A questo punto, il package VS può offrire aggiornare il file al nuovo formato o aprire il file e mantenere la compatibilità con le versioni precedenti del package VS.  
  
> [!NOTE]
>  È possibile combinare questi approcci.  Ad esempio, è possibile garantire la compatibilità con le versioni precedenti caricando un file più recente e offrono migliorare il formato di file quando l'utente viene salvato.  
  
## Opposto al problema  
 Se si desidera Vspackage side\-by\-side più per utilizzare la stessa estensione, è necessario selezionare la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associata all'estensione.  Di seguito sono riportati due alternative:  
  
-   Aprire il file nella versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installato nel computer di un utente.  
  
     In questo modo, il programma di installazione è responsabile della determinazione della versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e di includere quello nella voce del Registro di sistema scritta per l'associazione di file.  In un package di Windows Installer, è possibile includere azioni personalizzate impostare una proprietà che indica la versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    > [!NOTE]
    >  In questo contesto, “i„ significa “ultima versione supportata.„ Queste voci del programma di installazione automatica non rileveranno una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Le voci di [Rilevamento dei requisiti di sistema](../extensibility/internals/detecting-system-requirements.md) e di [Comandi devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md) sono simili a quelle riportate qui e sono necessarie supportare le versioni aggiuntive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Le seguenti righe della tabella CustomAction impostare la proprietà di DEVENV\_EXE\_LATEST per essere un insieme di proprietà dalle tabelle di RegLocator e di AppSearch descritte in [Comandi devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md).  Le righe della tabella di InstallExecuteSequence pianificano le azioni personalizzate precedenza nella sequenza di esecuzione.  I valori nella colonna della condizione consentono di logica:  
  
    -   Visual Studio .NET 2002. è la versione più recente se è l'unica versione corrente.  
  
    -   Visual Studio .NET 2003. è la versione più recente solo se è presente e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è presente.  
  
    -   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è la versione più recente se è l'unica versione corrente.  
  
     Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>,  e deve eseguire l'override dei metodi <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>.  
  
    ### Righe della tabella CustomAction che determinano la versione più recente di Visual Studio  
  
    |Azione|Type|Origine|Destinazione|  
    |------------|----------|-------------|------------------|  
    |CA\_SetDevenvLatest\_2002|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2002\]|  
    |CA\_SetDevenvLatest\_2003|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2003\]|  
    |CA\_SetDevenvLatest\_2005|51|DEVENV\_EXE\_LATEST|\[DEVENV\_EXE\_2005\]|  
  
    ### Righe della tabella di InstallExecuteSequence che determinano la versione più recente di Visual Studio  
  
    |Azione|Condizione|sequenza|  
    |------------|----------------|--------------|  
    |CA\_SetDevenvLatest\_2002|DEVENV\_EXE\_2002 L'OPERAZIONE NOT \(DEVENV\_EXE\_2003 OR DEVENV\_EXE\_2005\)|410|  
    |CA\_SetDevenvLatest\_2003|DEVENV\_EXE\_2003 L'OPERAZIONE NOT DEVENV\_EXE\_2005|420|  
    |CA\_SetDevenvLatest\_2005|DEVENV\_EXE\_2005|430|  
  
     È possibile utilizzare la proprietà di DEVENV\_EXE\_LATEST nella tabella del Registro Di Sistema del pacchetto di Windows Installer per scrivere il HKEY\_CLASSES\_ROOT \\*ProgId*\\Shell\\Open\\Command key's default value, \[DEVENV\_EXE\_LATEST\] “%1 "  
  
-   Eseguire un programma condiviso di avvio che può effettuare la scelta migliore dalle versioni disponibili di un VSPackage.  
  
     Gli sviluppatori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] scelto questo approccio per gestire i requisiti complessi dei formati diversi di soluzioni e progetti in tale risultato da diverse versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  In questo approccio, si registra un programma di avvio come gestore dell'estensione.  Il avvio esaminato il file e decide quale la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il package VS possono gestire specifico archiviare.  Ad esempio, se un utente apre un file che è stato salvato per ultimo da una determinata versione del package VS, il avvio possibile avviare che VSPackage nella versione corrispondente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Inoltre, è possibile configurare il avvio per avviare sempre la versione più recente.  Un avvio anche potrebbe richiedere un utente a migliorare il formato del file.  Se il formato del file include un numero di versione, il avvio potrebbe inviare un utente se il formato di file appartiene a una versione successiva a uno o più del package VS installato.  
  
     Il avvio deve trovarsi in un componente di Windows Installer che è condivisa con tutte le versioni del package VS.  Questo processo assicura che la versione più recente sia installata sempre e non viene rimosso fino a disinstallare le versioni del package VS.  In questo modo, le associazioni di file e altre voci del Registro di sistema del componente di avvio vengono mantenute anche se la versione del package VS viene disinstallata.  
  
## disinstallare e associazioni di file  
 Disinstallazione di un package VS che scrive le voci del Registro di sistema per le associazioni di file cancella le associazioni di file.  di conseguenza, l'estensione non ha programmi associati.  Windows Installer “non recupera„ voci del Registro di sistema che sono stati aggiunti quando il package VS è stato installato.  Di seguito sono elencati alcuni modi per correggere le associazioni di file di un utente:  
  
-   Utilizzare un componente condiviso di avvio come sopra descritta.  
  
-   Configurare l'utente eseguire un ripristino della versione del package VS che il consumer deve essere inclusa l'associazione di file.  
  
-   Fornire un programma eseguibile separato che riscrive le voci del Registro di sistema appropriate.  
  
-   Immettere le opzioni di configurazione pagina o finestra di dialogo che consentono agli utenti di scegliere le associazioni di file e recuperare le associazioni perse.  Indicare agli utenti di eseguirlo dopo la disinstallazione.  
  
## Vedere anche  
 [Registrazione di estensioni di File per le distribuzioni Side\-By\-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [La registrazione di verbi di estensioni di File](../extensibility/registering-verbs-for-file-name-extensions.md)