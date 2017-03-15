---
title: "Procedura: installare un plug-in del controllo del codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazione [Visual Studio SDK], plug-in del controllo codice sorgente"
  - "origine plug-in del controllo, l'installazione"
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Procedura: installare un plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Creazione di plug-in un controllo origine prevede tre passaggi:  
  
1.  Creare una DLL con le funzioni definite nella sezione di riferimento API plug-in controllo di origine di questa documentazione.  
  
2.  Implementare le funzioni definite dall'API dei plug-in controllo di origine. Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le chiamate a disposizione le interfacce e le finestre di dialogo il plug-in.  
  
3.  Registrare la DLL, rendendo le voci del Registro di sistema.  
  
## <a name="integration-with-visual-studio"></a>Integrazione con Visual Studio  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta plug-in di controllo di origine che è conforme all'API di plug-in controllo di origine.  
  
### <a name="registering-the-source-control-plug-in"></a>Registrare il plug-in del controllo del codice sorgente  
 Prima che possa chiamare un ambiente di sviluppo integrato (IDE) in esecuzione nel sistema di controllo di origine, è necessario innanzitutto trovare l'origine DLL plug-in che consente di esportare l'API di controllo.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Per registrare il controllo origine DLL plug-in  
  
1.  Aggiungere due voci sotto la chiave HKEY_LOCAL_MACHINE nella sottochiave del SOFTWARE che specifica la sottochiave nome società aggiungendo la sottochiave nome prodotto. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\\*[nome della società]*\\*[nome prodotto]*\\*[entry]* = valore. Le due voci sono chiamate sempre SCCServerName e SCCServerPath. Ognuno è una stringa normale.  
  
     Ad esempio, se il nome della società è Microsoft e il prodotto del controllo codice sorgente denominato SourceSafe, il percorso del Registro di sistema sarebbe HKEY_LOCAL_MACHINE\Software\Microsoft\SourceSafe.. In questa sottochiave, la prima voce, SCCServerName, è una stringa leggibile dall'utente di denominazione del prodotto. La seconda voce, SCCServerPath, è il percorso completo all'origine del controllo DLL plug-in dell'IDE deve connettersi a. Nelle sezioni che seguono vengono fornite le voci del Registro di sistema di esempio:  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    >  Il SCCServerPath è il percorso completo per il plug-in SourceSafe. Controllo del codice sorgente del plug-in utilizzerà i nomi di società e prodotti diversi ma gli stessi percorsi voce del Registro di sistema.  
  
2.  Le seguenti voci del Registro di sistema facoltativo consente di modificare il comportamento del controllo del codice sorgente del plug-in. Queste voci passare nella stessa sottochiave SccServerName e SccServerPath.  
  
    -   Se non si desidera l'origine controllo dei plug-in venga visualizzato nell'elenco di selezione plug-in è possibile utilizzare la voce HideInVisualStudioregistry [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Questa voce avrà effetto anche sul passaggio automatico per il plug-in del controllo del codice sorgente. Un possibile utilizzo di questa voce è se si fornisce un pacchetto di controllo di origine che sostituisce il plug-in del controllo del codice sorgente ma si desidera semplificare per l'utente eseguire la migrazione dall'utilizzo del controllo di origine del plug-in per il pacchetto di controllo di origine. Quando viene installato il pacchetto di controllo di origine, imposta questa voce del Registro di sistema, che nasconde il plug-in.  
  
         HideInVisualStudio è un valore DWORD ed è impostato su 1 per nascondere il plug-in o 0 per visualizzare il plug-in. Se non viene visualizzata la voce del Registro di sistema, il comportamento predefinito è mostrare il plug-in.  
  
    -   La voce del Registro di sistema DisableSccManager può essere utilizzata per disabilitare o nascondere il **avviare \< Server di origine del controllo>** opzione di menu che viene in genere visualizzata sotto il **File** -> **controllo del codice sorgente** sottomenu. Selezionare questo menu opzione chiamate di [SccRunScc](../../extensibility/sccrunscc-function.md) (funzione). Plug-in del controllo del codice sorgente non supportino un programma esterno e pertanto è consigliabile disabilitare o nascondere anche le **avviare** opzione di menu.  
  
         DisableSccManager è un valore DWORD è impostato su 0 per abilitare il **avviare \< Server di origine del controllo>** opzione di menu, impostare su 1 per disabilitare l'opzione di menu e impostato su 2 per nascondere l'opzione di menu. Se questa voce del Registro di sistema non viene visualizzato, il comportamento predefinito è mostrare l'opzione di menu.  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3.  Aggiungere la sottochiave SourceCodeControlProvider, sotto la chiave HKEY_LOCAL_MACHINE nella sottochiave del SOFTWARE.  
  
     In questa sottochiave è impostata la voce del Registro di sistema ProviderRegKey a una stringa che rappresenta la sottochiave che è stato inserito nel Registro di sistema nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey = SOFTWARE\\*[nome della società]*\\*[nome prodotto]*.  
  
     Di seguito è riportato il contenuto di esempio per questa sottochiave.  
  
    |Voce del Registro di sistema|Valore di esempio|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Controllo del codice sorgente del plug-in utilizzerà la stessa sottochiave e i nomi di voce, ma il valore sarà diverso.  
  
4.  Creare una sottochiave denominata InstalledSCCProviders nella sottochiave SourceCodeControlProvider e quindi inserire una voce in tale sottochiave.  
  
     Il nome di questa voce è il nome leggibile dall'utente del provider (uguale al valore specificato per la voce SCCServerName) e il valore è, ancora una volta, la sottochiave creata nel passaggio 1. Il modello è HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\\*[nome]* = SOFTWARE\\*[nome della società]*\\*[nome prodotto]*.  
  
     Ad esempio:  
  
    |Voce del Registro di sistema di esempio|Valore di esempio|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    >  Possono essere presenti più origine plug-in del controllo registrato in questo modo. Ecco come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Trova installati tutti i plug-in basato su API plug-in controllo di origine.  
  
## <a name="how-an-ide-locates-the-dll"></a>Modalità di individuazione della DLL di un IDE  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE dispone di due metodi per individuare l'origine controllano DLL plug-in:  
  
-   Individuare il controllo del codice sorgente predefinito plug-in e connettersi automaticamente.  
  
-   Trovare origine registrata tutti plug-in del controllo, da cui l'utente sceglie uno.  
  
 Per individuare la DLL il primo modo, l'IDE di ricerca nella sottochiave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider per la voce ProviderRegKey. Il valore di questa voce punta a un'altra sottochiave. L'IDE cerca una voce denominata SccServerPath nella sottochiave secondo in HKEY_LOCAL_MACHINE. Il valore di questa voce fa riferimento l'IDE alla DLL.  
  
> [!NOTE]
>  L'IDE non caricare le DLL da percorsi relativi (ad esempio,.\NewProvider.DLL). Specificare un percorso completo della DLL (ad esempio, c:\Providers\NewProvider.DLL). Ciò aumenta la protezione dell'IDE impedendo il caricamento delle DLL plug-in utenti non autorizzati o rappresentato.  
  
 Per individuare la DLL il secondo modo, l'IDE cerca nella sottochiave HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders per tutte le voci*.* Ogni voce ha un nome e un valore. L'IDE visualizza un elenco di questi nomi per l'utente*.* Quando l'utente sceglie un nome, l'IDE consente di trovare il valore per il nome selezionato che punta a una sottochiave. L'IDE cerca una voce denominata SccServerPath nella sottochiave in HKEY_LOCAL_MACHINE. Il valore della voce punta IDE alla DLL corretta.  
  
 Un plug-in del controllo del codice sorgente deve supportare entrambi i metodi di individuazione della DLL e, di conseguenza, impostare ProviderRegKey, sovrascrivendo qualsiasi impostazione precedente. Ancora più importante, deve aggiungere se stesso all'elenco di InstalledSccProviders l'utente può avere una scelta di quale plug-in del controllo del codice sorgente da utilizzare.  
  
> [!NOTE]
>  Poiché viene utilizzata la chiave HKEY_LOCAL_MACHINE, controllo del codice sorgente di un solo plug-in può essere registrato come controllo di origine predefinito plug-in un determinato computer (tuttavia, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consente agli utenti di determinare quale controllo codice sorgente che desiderano utilizzare effettivamente per una particolare soluzione). Durante il processo di installazione, verificare se è già impostato un plug-in del controllo del codice sorgente; In questo caso, chiedere all'utente di impostare il controllo del codice sorgente nuovo plug-in viene installata come il valore predefinito o meno. Durante la disinstallazione, non rimuovere altre sottochiavi del Registro di sistema che sono comuni a tutti origine plug-in del controllo in HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider; rimuovere la specifica sottochiave SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Come l'IDE rileva il supporto della versione 1.2 o 1.3  
 Come viene [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rilevare la presenza di una funzionalità di plug-in supporta API plug-in controllo origine versione 1.2 e 1.3? Per dichiarare le funzionalità avanzate, il plug-in del controllo del codice sorgente deve implementare la funzione corrispondente.  
  
 Primo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Controlla il valore restituito dalla chiamata di [SccGetVersion](../../extensibility/sccgetversion-function.md). Deve essere maggiore o uguale a 1.2.  
  
 Successivamente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] determina se è supportata la nuova funzionalità particolare esaminando il `lpSccCaps` argomento per il [SccInitialize](../../extensibility/sccinitialize-function.md).  
  
 Se entrambe le condizioni vengono soddisfatte, le nuove funzioni supportate nelle versioni 1.2 e 1.3 possono essere chiamate.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida introduttiva](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)