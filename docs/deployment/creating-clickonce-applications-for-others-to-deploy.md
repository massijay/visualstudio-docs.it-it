---
title: "Creating ClickOnce Applications for Others to Deploy | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "preserved branding information"
  - "useManifestForTrust element"
  - "customer deployments [ClickOnce]"
  - "multiple ClickOnce deployment and branding"
  - "ClickOnce applications, previous .NET Framework versions"
  - "application manifests [ClickOnce]"
  - "<useManifestForTrust> element"
  - "manifests [ClickOnce]"
  - "trust applications, ClickOnce"
  - "ClickOnce applications, deployed by others"
  - "ClickOnce applications, previous .NET Framework"
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Creating ClickOnce Applications for Others to Deploy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Non tutti gli sviluppatori che creano distribuzioni ClickOnce intendono provvedere personalmente alla relativa distribuzione.  Molti di essi assemblano semplicemente l'applicazione utilizzando ClickOnce e successivamente affidano i file a un cliente esterno quale una grande azienda.  Il cliente dunque si assume la responsabilità di ospitare l'applicazione nella propria rete.  In questo argomento vengono illustrati alcuni problemi relativi a questi tipi di distribuzione nelle versioni di .NET Framework precedenti alla versione 3.5.  Viene quindi descritta una soluzione innovativa disponibile grazie alla nuova funzionalità "Usa manifesto applicazione per informazioni sull'attendibilità" di .NET Framework 3.5.  Vengono infine consigliate strategie per la creazione di distribuzioni ClickOnce per clienti che utilizzano ancora versioni precedenti di .NET Framework.  
  
## Problemi relativi alla creazione di distribuzioni per i clienti  
 Quando si programma di fornire una distribuzione a un cliente, si verificano diversi problemi.  Il primo problema riguarda la firma del codice.  Per poter essere distribuito attraverso una rete, il manifesto di distribuzione e il manifesto dell'applicazione di una distribuzione ClickOnce devono essere firmati entrambi con un certificato digitale.  Tale requisito comporta la necessità di scegliere se utilizzare il certificato dello sviluppatore o il certificato del cliente per la firma dei manifesti.  
  
 Questa decisione è di fondamentale importanza in quanto l'identità dell'applicazione ClickOnce si basa sulla firma digitale del manifesto di distribuzione.  Se lo sviluppatore firma il manifesto di distribuzione, potrebbero verificarsi conflitti se il cliente è un'azienda di grandi dimensioni e più reparti di tale azienda distribuiscono una versione personalizzata dell'applicazione.  
  
 Si supponga ad esempio che Adventure Works disponga di un reparto contabile e di un reparto risorse umane.  Entrambi i reparti concedono in licenza un'applicazione ClickOnce di Microsoft Corporation che genera report dai dati memorizzati in un database SQL.  Microsoft fornisce a ogni reparto una versione dell'applicazione personalizzata per i rispettivi dati.  Se le applicazioni vengono firmate con lo stesso certificato Authenticode, un utente che prova a utilizzarle entrambe riscontrerà un errore, in quanto ClickOnce considera la seconda applicazione identica alla prima.  In questo caso, il cliente potrebbe subire effetti collaterali imprevedibili e indesiderati, inclusa la perdita dei dati memorizzati localmente dall'applicazione.  
  
 Un problema aggiuntivo relativo alla firma del codice è rappresentato dall'elemento `deploymentProvider` nel manifesto di distribuzione, che indica a ClickOnce la posizione in cui cercare eventuali aggiornamenti dell'applicazione.  Tale elemento deve essere aggiunto al manifesto di distribuzione prima di apporvi una firma.  Se viene aggiunto successivamente, è necessario firmare nuovamente il manifesto di distribuzione.  
  
### Richiesta della firma del manifesto di distribuzione da parte del cliente  
 Per risolvere il problema delle distribuzioni non univoche è possibile richiedere allo sviluppatore di firmare il manifesto dell'applicazione e al cliente di firmare il manifesto di distribuzione.  Questo approccio funziona ma purtroppo introduce altri problemi.  Poiché il certificato Authenticode deve rimanere una risorsa protetta, il cliente non può solo fornire il certificato allo sviluppatore per la firma della distribuzione.  Sebbene il cliente possa firmare autonomamente il manifesto di distribuzione utilizzando gli strumenti disponibili gratuitamente in .NET Framework SDK, questa operazione potrebbe richiedere competenze tecniche non sempre garantite da tutti i clienti.  In tali casi, lo sviluppatore in genere crea un'applicazione, un sito Web o un altro meccanismo grazie al quale il cliente può inviare la propria versione dell'applicazione per la firma.  
  
### Impatto della firma del cliente sulla sicurezza dell'applicazione ClickOnce  
 Anche se lo sviluppatore e il cliente concordano sulla necessità di assegnare al cliente il compito di firmare il manifesto dell'applicazione, questa soluzione genera altri problemi relativi all'identità dell'applicazione stessa, in particolare quando si lavora a una distribuzione di applicazioni attendibili.  Per ulteriori informazioni su questa funzionalità, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md). Si supponga che Adventure Works desideri configurare i propri computer client in modo da poter eseguire le applicazioni fornite da Microsoft Corporation con attendibilità totale.  Se Adventure Works firma il manifesto di distribuzione, ClickOnce utilizzerà la firma di sicurezza di Adventure Work per determinare il livello di attendibilità dell'applicazione.  
  
## Creazione di distribuzioni del cliente utilizzando il manifesto dell'applicazione per l'attendibilità  
 ClickOnce di .NET Framework 3.5 contiene una nuova funzionalità che offre a sviluppatori e clienti una nuova soluzione per la firma dei manifesti.  Il manifesto dell'applicazione ClickOnce supporta un nuovo elemento denominato `<useManifestForTrust>` che consente agli sviluppatori di comunicare che la firma digitale del manifesto dell'applicazione deve essere utilizzata per prendere decisioni sull'attendibilità.  Lo sviluppatore utilizza gli strumenti di assemblaggio ClickOnce, quali Mage.exe, MageUI.exe e Visual Studio, per includere questo elemento nel manifesto dell'applicazione, nonché per incorporare il nome dell'Editore e il nome dell'applicazione nel manifesto.  
  
 Quando si utilizza `<useManifestForTrust>`, il manifesto di distribuzione non deve essere firmato con un certificato Authenticode emesso da un'Autorità di certificazione.  Può essere invece firmato con un certificato autofirmato.  Un certificato autofirmato viene generato dal cliente o dallo sviluppatore utilizzando gli strumenti .NET Framework SDK standard e viene quindi applicato al manifesto di distribuzione utilizzando gli strumenti di distribuzione ClickOnce standard.  Per ulteriori informazioni, vedere [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md).  
  
 L'utilizzo di un certificato autofirmato per il manifesto di distribuzione presenta molti vantaggi.  `<useManifestForTrust>` semplifica la procedura di distribuzione in quanto elimina la necessità per il cliente di ottenere o creare il proprio certificato Authenticode e al tempo stesso consente allo sviluppatore di conservare la propria identità personale sull'applicazione.  Il risultato è un insieme di distribuzioni firmate più sicure e con identità di applicazione univoche.  In questo modo si evitano i potenziali conflitti derivati dalla distribuzione della stessa applicazione a più clienti.  
  
 Per informazioni dettagliate su come creare una distribuzione ClickOnce con la funzionalità `<useManifestForTrust>` attivata, vedere [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### Funzionamento del manifesto dell'applicazione per l'attendibilità in fase di esecuzione  
 Per comprendere meglio il funzionamento del manifesto dell'applicazione per l'attendibilità in fase di esecuzione, si consideri l'esempio seguente.  Microsoft crea un'applicazione ClickOnce destinata all'utilizzo con .NET Framework 3.5.  Il manifesto dell'applicazione utilizza l'elemento `<useManifestForTrust>` e viene firmato da Microsoft.  Adventure Works firma il manifesto di distribuzione utilizzando un certificato autofirmato.  I client Adventure Works vengono configurati in modo da considerare attendibili tutte le applicazioni firmate da Microsoft.  
  
 Quando un utente fa clic su un collegamento al manifesto di distribuzione, ClickOnce installa l'applicazione nel computer dell'utente.  Grazie al certificato e alle informazioni sulla distribuzione, ClickOnce sul computer client è in grado di identificare in modo univoco l'applicazione.  Se l'utente prova a installare nuovamente la stessa applicazione da un percorso differente, ClickOnce può utilizzare tale identità per stabilire che l'applicazione è già presente sul client.  
  
 Successivamente, ClickOnce esaminerà il certificato Authenticode utilizzato per firmare il manifesto dell'applicazione, in modo da determinare il livello di attendibilità da concedere.  Poiché Adventure Works ha configurato i propri client in modo da considerare attendibili tutte le applicazioni firmate da Microsoft, a questa applicazione ClickOnce viene concessa l'attendibilità totale.  Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
## Creazione di distribuzioni del cliente per le versioni precedenti  
 Si supponga che uno sviluppatore distribuisca applicazioni ClickOnce a clienti che utilizzano versioni precedenti di .NET Framework.  Nelle sezioni seguenti sono riepilogate diverse soluzioni consigliate, insieme con i vantaggi e gli svantaggi di ciascuna di esse.  
  
### Firmare le distribuzioni per conto del cliente  
 Una strategia di distribuzione possibile prevede che lo sviluppatore crei un meccanismo atto a firmare distribuzioni per conto dei propri clienti utilizzando la chiave privata del cliente.  In questo modo lo sviluppatore non dovrà gestire più pacchetti di distribuzione o chiavi private.  È sufficiente che lo sviluppatore fornisca la stessa distribuzione a ogni cliente.  Sarà compito del cliente personalizzarla per il proprio ambiente utilizzando il servizio di firma.  
  
 Questo metodo presenta lo svantaggio di richiedere tempi e costi eccessivi per la relativa implementazione.  Sebbene sia possibile compilare un servizio utilizzando gli strumenti forniti con .NET Framework SDK, il ciclo di vita del prodotto richiederà tempi di sviluppo maggiori.  
  
 Come notato prima in questo argomento, un altro inconveniente è rappresentato dal fatto che la versione dell'applicazione fornita a ogni cliente presenterà la stessa identità e pertanto si correrà il rischio di generare conflitti.  Se questo aspetto rappresenta un problema, lo sviluppatore può modificare il campo Nome utilizzato durante la generazione del manifesto di distribuzione per assegnare a ogni applicazione un nome univoco.  In questo modo verrà creata un'identità separata per ogni versione dell'applicazione e verranno eliminati i possibili conflitti di identità.  Questo campo corrisponde all'argomento `-Name` di Mage.exe e al campo **Nome** nella scheda **Nome** di MageUI.exe.  
  
 Si supponga, ad esempio, che lo sviluppatore abbia creato un'applicazione denominata Applicazione1.  Anziché creare un'unica distribuzione con il campo Nome impostato su Applicazione1, lo sviluppatore può creare diverse distribuzioni con una variante specifica del cliente per questo nome, ad esempio Applicazione1\-ClienteA, Applicazione1\-ClienteB e così via.  
  
### Distribuire utilizzando un package di installazione  
 Una seconda strategia di distribuzione possibile consiste nel generare un progetto di installazione Microsoft per l'esecuzione della distribuzione iniziale dell'applicazione ClickOnce.  Tale progetto può essere fornito in uno dei diversi formati disponibili, ad esempio come distribuzione MSI, come file eseguibile di installazione \(con estensione EXE\) o come file cabinet \(con estensione cab\) insieme a uno script batch.  
  
 Grazie a questa tecnica, lo sviluppatore fornisce al cliente una distribuzione che include i file dell'applicazione, il manifesto dell'applicazione e un manifesto di distribuzione da utilizzare come modello.  Il cliente esegue il programma di installazione, che richiede un URL di distribuzione, ovvero il percorso del server o della condivisione file dal quale gli utenti installeranno l'applicazione ClickOnce, nonché un certificato digitale.  L'applicazione di installazione può anche scegliere di richiedere ulteriori opzioni di configurazione ClickOnce, ad esempio l'intervallo per il controllo degli aggiornamenti.  Dopo aver raccolto queste informazioni, il programma di installazione genera il manifesto di distribuzione effettivo, lo firma e quindi pubblica l'applicazione ClickOnce nel percorso server designato.  
  
 In una situazione del genere, il cliente può firmare il manifesto di distribuzione in tre modi differenti:  
  
1.  Il cliente può utilizzare un certificato valido emesso da un'Autorità di certificazione \(CA\).  
  
2.  Una variante di questo approccio prevede che il cliente scelga di firmare il manifesto di distribuzione con un certificato autofirmato.  Lo svantaggio è che l'applicazione visualizzerà il messaggio "Editore sconosciuto" quando all'utente verrà chiesto il percorso di installazione.  Il vantaggio tuttavia è rappresentato dalla possibilità di evitare ai piccoli clienti i tempi lunghi e i costi elevati necessari per l'emissione di un certificato da parte di un'Autorità di certificazione.  
  
3.  Lo sviluppatore può infine includere il proprio certificato autofirmato nel package di installazione.  Questo approccio introduce tuttavia i problemi potenziali relativi all'identità dell'applicazione descritti in precedenza nel presente argomento.  
  
 L'inconveniente del metodo basato sul progetto di distribuzione per l'installazione è rappresentato dai tempi e i costi necessari per la compilazione di un'applicazione di distribuzione personalizzata.  
  
### Richiedere la generazione del manifesto di distribuzione al cliente  
 Una terza strategia di distribuzione possibile consiste nell'affidare al cliente solo i file e il manifesto dell'applicazione.  In questo scenario il cliente è responsabile dell'utilizzo di .NET Framework SDK per la generazione e la firma del manifesto di distribuzione.  
  
 Questo metodo presenta l'inconveniente di presupporre che il cliente installi gli strumenti .NET Framework SDK e disponga di uno sviluppatore o di un amministratore di sistema in grado di utilizzarli.  Alcuni clienti richiedono invece soluzioni per il cui utilizzo sono necessarie competenze tecniche scarse o nulle.  
  
## Vedere anche  
 [Deploying ClickOnce Applications For Testing and Production Servers without Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)