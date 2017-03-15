---
title: "Server and Client Configuration Issues in ClickOnce Deployments | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "deploying applications, ClickOnce"
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
  - "Windows applications, ClickOnce deployments"
ms.assetid: 929e5fcc-dd56-409c-bb57-00bd9549b20b
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Server and Client Configuration Issues in ClickOnce Deployments
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si utilizza Internet Information Services \(IIS\) in Windows Server e la distribuzione contiene un tipo di file non riconosciuto da Windows, ad esempio un file di Microsoft Word, la trasmissione del file non sarà consentita e verrà generato un errore durante la distribuzione.  
  
 Inoltre, determinati server Web e software applicativi Web, ad esempio [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], contengono un elenco di file e tipi di file di cui non è consentito il download.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], ad esempio, impedisce il download di tutti i file Web.config.  Tali file possono contenere informazioni riservate quali i nomi utente e le password.  
  
 Anche se questa limitazione non causa in genere problemi per il download dei file più importanti di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ad esempio manifesti e assembly, può impedire il download di file di dati inclusi nell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  In [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è possibile risolvere questo errore rimuovendo il gestore che impedisce il download di questi file da Gestione configurazione IIS.  Per ulteriori informazioni, vedere la documentazione relativa al server IIS.  
  
 È possibile che alcuni server Web blocchino i file con estensioni dll, config e mdf.  Nelle applicazioni per Windows, tuttavia, sono normalmente inclusi file con queste estensioni.  Se quindi un utente prova a eseguire un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che deve accedere a un file bloccato su un server Web, verrà restituito un errore.  Per evitare che vengano sbloccate tutte le estensioni di file, per impostazione predefinita ogni file di applicazione viene pubblicato da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con estensione deploy.  L'amministratore pertanto dovrà solo configurare il server Web per sbloccare le tre estensioni di file seguenti:  
  
-   .application  
  
-   .manifest  
  
-   deploy  
  
 È tuttavia possibile disabilitare questa opzione deselezionando la casella di controllo **Usa estensione ".deploy"** nella [Publish Options Dialog Box](http://msdn.microsoft.com/it-it/fd9baa1b-7311-4f9e-8ffb-ae50cf110592). In tal caso sarà necessario configurare il server Web in modo da sbloccare tutte le estensioni di file utilizzate nell'applicazione.  
  
 Sarà ad esempio necessario configurare le estensioni manifest, application e deploy se si utilizza una versione di IIS in cui non è stato installato [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] oppure se si utilizza un altro server Web quale Apache.  
  
## ClickOnce e SSL \(Secure Sockets Layer\)  
 Un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funziona correttamente su SSL, ad eccezione dei casi in cui Internet Explorer genera una richiesta sul certificato SSL.  Tale richiesta può essere generata se il certificato presenta dei problemi, ad esempio se i nomi dei siti non corrispondono o se il certificato è scaduto.  Per far sì che [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funzioni su una connessione SSL, accertarsi che il certificato sia aggiornato e che i dati del certificato corrispondano ai dati del sito.  
  
## ClickOnce e autenticazione proxy  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] fornisce supporto per l'autenticazione del proxy integrata di Windows a partire da .NET Framework 3.5.  Non sono richieste specifiche direttive machine.config.  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non fornisce supporto per altri protocolli di autenticazione come Basic o Digest.  
  
 È inoltre possibile applicare un aggiornamento rapido a .NET Framework 2.0 per abilitare questa funzionalità.  Per ulteriori informazioni, vedere http:\/\/go.microsoft.com\/fwlink\/?LinkId\=158730.  
  
 Per ulteriori informazioni, vedere [Elemento \<defaultProxy\> \(Impostazioni di rete\)](../Topic/%3CdefaultProxy%3E%20Element%20\(Network%20Settings\).md).  
  
## ClickOnce e compatibilità con i browser Web  
 Le installazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] attualmente si avviano solo se l'URL del manifesto di distribuzione viene aperto utilizzando Internet Explorer.  Una distribuzione il cui URL viene avviato da un'altra applicazione, ad esempio Microsoft Office Outlook, si avvierà solo se Internet Explorer è impostato come browser Web predefinito.  
  
> [!NOTE]
>  Mozilla Firefox è supportato se il provider di distribuzione non è vuoto ed è installata l'estensione Microsoft .NET Framework Assistant.  Questa estensione è inclusa in .NET Framework 3.5 SP1.  Per il supporto di XBAP, viene attivato il plug\-in NPWPF quando necessario.  
  
## Attivazione delle applicazioni ClickOnce tramite scripting di browser  
 Se è stata sviluppata una pagina Web personalizzata che avvia un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] con scripting attivo, è possibile che in alcuni computer l'applicazione non si avvii.  In Internet Explorer è disponibile un'impostazione denominata **Richiesta di conferma automatica per download di file** che influisce su questo comportamento.  Questa impostazione è disponibile nella Scheda **Sicurezza** nel menu **Opzioni** che influisce su questo comportamento.  È denominata **Richiesta di conferma automatica per download di file** ed è elencata sotto la categoria **Download**.  Per impostazione predefinita, la proprietà è impostata su **Attiva** per le pagine Web Intranet e su **Disabilita** per le pagine Web Internet.  Quando questa impostazione è impostata su **Disabilita**, qualsiasi tentativo di attivare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] a livello di codice \(ad esempio, assegnando il relativo URL alla proprietà `document.location`\) verrà bloccato.  In queste circostanze, gli utenti possono avviare applicazioni solo tramite un download iniziato dall'utente, ad esempio, facendo clic su un insieme di collegamenti ipertestuali all'URL dell'applicazione.  
  
## Altri problemi relativi alla configurazione del server  
  
##### Autorizzazioni dell'amministratore richieste  
 È necessario disporre delle autorizzazioni di amministratore sul server di destinazione se si esegue la pubblicazione con HTTP.  IIS richiede questo tipo di autorizzazione.  Se invece non si utilizza HTTP, è necessario disporre solo dell'autorizzazione di scrittura sul percorso di destinazione.  
  
##### Problemi relativi all'autenticazione del server  
 Quando si pubblica in un server remoto con l'accesso anonimo disabilitato, viene visualizzato il seguente avviso:  
  
```  
"The files could not be downloaded from http://<remoteserver>/<myapplication>/.  The remote server returned an error: (401) Unauthorized."  
```  
  
> [!NOTE]
>  È possibile far funzionare l'autenticazione NTLM \(In attesa\/Risposta NT\) se il sito chiede credenziali diverse rispetto a quelle predefinite, e, nella finestra di dialogo relativa alla sicurezza, si sceglie **OK** per salvare le credenziali fornite per le sessioni future.  Questa soluzione tuttavia non è efficace per l'autenticazione di base.  
  
## Utilizzo di server Web di terze parti  
 Quando si distribuisce un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da un server Web diverso da IIS, è possibile che si verifichi un problema se il server restituisce il tipo di contenuto non corretto per i file [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] più importanti, ad esempio il manifesto di distribuzione e quello dell'applicazione.  Per risolvere questo problema, vedere la documentazione del server Web sull'aggiunta di nuovi tipi di contenuto al server e assicurarsi che siano presenti tutti i mapping delle estensioni dei nomi di file elencati nella tabella riportata di seguito.  
  
|Estensione del nome file|Tipo di contenuto|  
|------------------------------|-----------------------|  
|`.application`|`application/x-ms-application`|  
|`.manifest`|`application/x-ms-manifest`|  
|`.deploy`|`application/octet-stream`|  
|`.msu`|`application/octet-stream`|  
|`.msp`|`application/octet-stream`|  
  
## ClickOnce e unità mappate  
 Se si utilizza Visual Studio per pubblicare un'applicazione ClickOnce, non è possibile specificare un'unità mappata come percorso di installazione.  Tuttavia, è possibile modificare l'applicazione ClickOnce per eseguire l'installazione da un'unità mappata tramite il generatore del manifesto e l'editor \(Mage.exe e MageUI.exe\).  Per ulteriori informazioni, vedere [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md) e [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  
  
## Protocollo FTP non supportato per l'installazione di applicazioni  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supporta l'installazione di applicazioni da qualsiasi file server o server Web HTTP 1.1.  Il protocollo FTP non è supportato per l'installazione di applicazioni.  È possibile utilizzare il protocollo FTP solo per pubblicare applicazioni.  Nella tabella riportata di seguito sono riepilogate tali differenze.  
  
|Tipo URL|Descrizione|  
|--------------|-----------------|  
|ftp:\/\/|È possibile pubblicare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizzando questo protocollo.|  
|http:\/\/|È possibile installare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizzando questo protocollo.|  
|https:\/\/|È possibile installare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizzando questo protocollo.|  
|file:\/\/|È possibile installare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizzando questo protocollo.|  
  
## Windows XP SP2: Windows Firewall  
 Per impostazione predefinita, Windows Firewall è attivato in Windows XP SP2.  Se si sviluppa un'applicazione in un computer con sistema operativo Windows XP, sarà possibile pubblicare ed eseguire applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dal server IIS locale,  ma non sarà possibile accedere al server che esegue IIS da un altro computer a meno che non venga aperto Windows Firewall.  Per istruzioni sulla gestione di Windows Firewall, vedere la Guida di Windows.  
  
## Windows Server: abilitazione delle estensioni del server di FrontPage  
 Per pubblicare applicazioni in un server Web Windows che utilizza HTTP, sono necessarie le estensioni del server di FrontPage fornite da Microsoft.  
  
 Per impostazione predefinita, le estensioni del server di FrontPage non sono installate in Windows Server.  Se si desidera utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire la pubblicazione in un server Web Windows Server che utilizza HTTP con le estensioni del server di FrontPage, è necessario innanzitutto installare queste ultime.  Per l'esecuzione di questa operazione, in Windows Server è disponibile lo strumento Amministrazione server.  
  
## Windows Server: tipi di contenuto bloccati  
 Se IIS viene eseguito su [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)], vengono bloccati tutti i tipi di file tranne alcuni tipi di contenuto noti, ad esempio htm, html, txt e così via.  Per consentire la distribuzione di applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tramite questo server, è quindi necessario modificare le impostazioni di IIS per consentire il download dei file con estensione application e manifest e di eventuali altri tipi di file personalizzati utilizzati nell'applicazione.  
  
 Se si effettua la distribuzione tramite un server IIS, eseguire inetmgr.exe e aggiungere nuovi tipi di file per la pagina Web predefinita:  
  
-   Per le estensioni application e manifest, il tipo MIME deve essere "application\/x\-ms\-application". Per altri tipi di file, il tipo MIME deve essere "application\/octet\-stream".  
  
-   Se si crea un tipo di file con estensione "\*" e tipo MIME "application\/octet\-stream", sarà possibile scaricare file il cui tipo è sbloccato.  I tipi di file bloccati, ad esempio quelli con estensione aspx e asmx, non potranno comunque essere scaricati.  
  
 Per istruzioni specifiche sulla configurazione dei tipi MIME in Windows Server, fare riferimento all'articolo KB326965, della Microsoft Knowledge Base, "IIS 6.0 non fornisce tipi MIME sconosciuti" all'indirizzo [http:\/\/support.microsoft.com\/kb\/326965\/it](http://support.microsoft.com/kb/326965/it).  
  
## Mapping dei tipi di contenuto  
 Quando si pubblica un'applicazione tramite HTTP, il tipo di contenuto, conosciuto anche come tipo MIME, relativo al file con estensione application deve essere "application\/x\-ms\-application". Se nel server è installato [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], questo tipo verrà impostato automaticamente.  In caso contrario, sarà necessario creare un'associazione al tipo MIME per la radice virtuale dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ossia per l'intero server.  
  
 Se si effettua la distribuzione utilizzando un server IIS, eseguire inetmgr.exe e aggiungere un nuovo tipo di contenuto "application\/x\-ms\-application" per l'estensione application.  
  
## Problemi relativi alla compressione HTTP  
 In [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è possibile eseguire il download con compressione HTTP, una tecnologia per server Web basata sull'algoritmo GZIP che consente di comprimere un flusso di dati prima di inviarli al client.  Il flusso viene poi decompresso dal client, nel caso specifico [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], prima della lettura dei file.  
  
 Se si utilizza IIS, è possibile attivare facilmente la compressione HTTP,  ma questa viene attivata solo per determinati tipi di file, ossia file HTML e file di testo.  Per attivare la compressione per gli assembly \(dll\), i file XML \(xml\), i manifesti di distribuzione \(application\) e i manifesti delle applicazioni \(manifest\), è necessario aggiungere questi tipi di file all'elenco di tipi di file per la compressione in IIS.  Fino a quando non vengono aggiunti i tipi di file alla distribuzione, verranno compressi solo i file di testo e HTML.  
  
 Per istruzioni dettagliate su IIS, vedere [Come specificare i tipi di documenti aggiuntivi per la compressione HTTP](http://go.microsoft.com/fwlink/?LinkId=178459).  
  
## Vedere anche  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)