---
title: "Building ClickOnce Applications from the Command Line | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ClickOnce deployment, from command line"
  - "publishing"
  - "publishing, ClickOnce"
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Building ClickOnce Applications from the Command Line
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] è possibile compilare progetti dalla riga di comando, anche se sono stati creati nell'ambiente di sviluppo integrato \(IDE\).  Infatti, un progetto creato con [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] può essere ricompilato su un altro computer in cui è installato solo [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Questa caratteristica consente di ripetere una compilazione mediante un processo automatico, ad esempio in un sistema di compilazione centrale o tramite tecniche di scripting avanzate che non rientrano nell'ambito di compilazione del progetto stesso.  
  
## Utilizzo di MSBuild per riprodurre distribuzioni di applicazioni ClickOnce  
 Se chiamata dalla riga di comando, l'istruzione msbuild \/target:publish indica al sistema MSBuild di compilare il progetto e creare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nella cartella di pubblicazione.  Questa operazione equivale a selezionare il comando **Pubblica** nell'ambiente di sviluppo integrato.  
  
 Questo comando consente di eseguire msbuild.exe, il cui percorso è definito nella variabile di ambiente PATH del prompt dei comandi di Visual Studio.  
  
 Il parametro target indica a MSBuild la modalità di elaborazione del comando.  I valori disponibili per questo parametro sono build e publish.  Il valore build equivale a selezionare il comando Compila o a premere F5 nell'ambiente di sviluppo integrato.  Se si desidera soltanto compilare il progetto, è sufficiente digitare `msbuild`.  Infatti, build è il valore predefinito del parametro target per tutti i progetti generati da [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Pertanto non è necessario specificare in modo esplicito la destinazione della compilazione.  Di conseguenza, il comando `msbuild` è equivalente al comando `msbuild /target:build`.  
  
 Il comando `/target:publish` indica a MSBuild di richiamare la destinazione \(target\) di pubblicazione.  Quest'ultima dipende dalla destinazione di compilazione.  In altre parole, l'operazione di pubblicazione costituisce un superset dell'operazione di compilazione.  Se ad esempio si apporta una modifica a uno dei file di origine Visual Basic o C\#, l'assembly corrispondente verrà rigenerato automaticamente dall'operazione di pubblicazione.  
  
 Per informazioni sulla generazione di una distribuzione completa di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizzando lo strumento della riga di comando Mage.exe per creare il manifesto di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vedere [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Creazione e compilazione di un'applicazione ClickOnce di base mediante MSBuild  
  
#### Per creare e pubblicare un progetto ClickOnce  
  
1.  Scegliere **Nuovo progetto** dal menu **File**.  Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  Selezionare **Applicazione Windows**, quindi assegnare al progetto il nome `CmdLineDemo`.  
  
3.  Scegliere **Pubblica** dal menu **Compila**.  
  
     In questo modo, il progetto verrà configurato correttamente in modo da generare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
     Verrà visualizzata la Pubblicazione guidata.  
  
4.  Nella Pubblicazione guidata scegliere **Fine**.  
  
     Verrà generata e visualizzata la pagina Web predefinita, denominata Publish.htm.  
  
5.  Salvare il progetto e prendere nota del percorso di cartella in cui è archiviato.  
  
 La procedura sopra riportata consente di creare un progetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che è stato pubblicato per la prima volta.  A questo punto è possibile ripetere la compilazione all'esterno dell'ambiente di sviluppo integrato.  
  
#### Per ripetere la compilazione dalla riga di comando  
  
1.  Chiudere [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
2.  Dal menu **Start** di Windows scegliere **Tutti i programmi**, **Microsoft Visual Studio**, **Visual Studio Tools**, quindi **Prompt dei comandi di Visual Studio**.  Verrà aperto un prompt dei comandi nella cartella radice dell'utente corrente.  
  
3.  Nella finestra **Prompt dei comandi di Visual Studio** spostarsi nel percorso contenente il progetto appena compilato.  Digitare, ad esempio, `chdir Documenti\Visual Studio\Projects\CmdLineDemo`.  
  
4.  Per rimuovere i file esistenti generati durante la procedura "Per creare e pubblicare un progetto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]", digitare `rmdir /s publish`.  
  
     Questo passaggio è facoltativo, ma garantisce che tutti i nuovi file siano stati creati mediante la compilazione dalla riga di comando.  
  
5.  Digitare `msbuild /target:publish`.  
  
 Mediante questa procedura verrà generata una distribuzione completa dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in una sottocartella del progetto denominata **Publish**.  CmdLineDemo.application è il manifesto di distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La cartella CmdLineDemo\_1.0.0.0 contiene i file CmdLineDemo.exe e CmdLineDemo.exe.manifest, ossia il manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Setup.exe è il programma di avvio automatico, che per impostazione predefinita è configurato per l'installazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  La cartella DotNetFX contiene i file ridistribuibili per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)],  necessari per la distribuzione dell'applicazione sul Web oppure tramite UNC o CD\/DVD.  
  
## Proprietà di pubblicazione  
 Quando viene pubblicata l'applicazione nelle procedure sopra riportate, durante l'esecuzione della Pubblicazione guidata verranno inserite nel file di progetto le seguenti proprietà,  che influiscono direttamente sul modo in cui verrà generata l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 In CmdLineDemo.vbproj \/ CmdLineDemo.csproj:  
  
```  
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>  
<GenerateManifests>true</GenerateManifests>  
<TargetZone>LocalIntranet</TargetZone>  
<PublisherName>Microsoft</PublisherName>  
<ProductName>CmdLineDemo</ProductName>  
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>  
<Install>true</Install>  
<ApplicationVersion>1.0.0.*</ApplicationVersion>  
<ApplicationRevision>1</ApplicationRevision>  
<UpdateEnabled>true</UpdateEnabled>  
<UpdateRequired>false</UpdateRequired>  
<UpdateMode>Foreground</UpdateMode>  
<UpdateInterval>7</UpdateInterval>  
<UpdateIntervalUnits>Days</UpdateIntervalUnits>  
<UpdateUrlEnabled>false</UpdateUrlEnabled>  
<IsWebBootstrapper>true</IsWebBootstrapper>  
<BootstrapperEnabled>true</BootstrapperEnabled>  
```  
  
 È possibile eseguire l'override di una qualsiasi di queste proprietà dalla riga di comando senza modificare il file di progetto stesso.  Ad esempio, per compilare la distribuzione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] senza il programma di avvio automatico è possibile utilizzare il seguente comando:  
  
```  
msbuild /target:publish /property:BootstrapperEnabled=false  
```  
  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le proprietà di pubblicazione possono essere definite nelle pagine delle proprietà **Pubblica**, **Sicurezza** e **Firma** di **Progettazione progetti**.  Di seguito è riportata la descrizione di ognuna di queste proprietà e viene indicato come impostare la proprietà nei riquadri appropriati di Progettazione progetti.  
  
-   `AssemblyOriginatorKeyFile` specifica il file di chiave utilizzato per firmare i manifesti dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Questa chiave può anche essere utilizzata per assegnare un nome sicuro agli assembly.  Questa proprietà viene impostata nella scheda **Firma** di **Progettazione progetti**.  
  
 Di seguito sono riportate le proprietà disponibili nella scheda **Sicurezza**.  
  
-   **Attiva le impostazioni di sicurezza ClickOnce** determina se i manifesti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verranno generati.  Al momento della creazione di un progetto, l'opzione di generazione del manifesto di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è disattivata per impostazione predefinita.  La prima volta che il progetto viene pubblicato mediante la procedura guidata, questo flag verrà attivato automaticamente.  
  
-   **TargetZone** determina il livello di attendibilità da definire nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  I valori possibili sono Internet, LocalIntranet e Custom.  Se si specifica Internet o LocalIntranet, nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà creato un insieme di autorizzazioni predefinito.  LocalIntranet è il valore predefinito e corrisponde al livello di attendibilità totale.  Il valore Custom specifica che nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] devono essere create soltanto le autorizzazioni indicate esplicitamente nel file app.manifest di base.  Quest'ultimo è un file di manifesto parziale contenente soltanto le definizioni delle informazioni sull'attendibilità.  Questo file è nascosto e viene aggiunto automaticamente al progetto quando si configurano le autorizzazioni nella scheda **Sicurezza**.  
  
 Di seguito sono riportate le proprietà disponibili nella scheda **Pubblica**.  
  
-   `PublishUrl` indica il percorso in cui verrà pubblicata l'applicazione nell'ambiente di sviluppo integrato.  Questo valore verrà inserito nel manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], se le proprietà `InstallUrl` e `UpdateUrl` non sono specificate.  
  
-   `ApplicationVersion` indica la versione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La versione è costituita da un numero a quattro cifre.  Se l'ultima cifra è un asterisco \(\*\), il valore inserito nel manifesto in fase di compilazione verrà sostituito con quello della proprietà `ApplicationRevision`.  
  
-   `ApplicationRevision` indica la revisione.  Si tratta di un intero che viene incrementato a ogni pubblicazione dell'applicazione nell'ambiente di sviluppo integrato.  Questo valore non viene incrementato automaticamente per le compilazioni eseguite dalla riga di comando.  
  
-   `Install` determina se l'applicazione deve essere installata o eseguita dal Web.  
  
-   `InstallUrl` \(non visualizzata\) indica il percorso da cui gli utenti eseguiranno l'installazione dell'applicazione.  Se specificato, questo valore verrà copiato nel programma di avvio automatico setup.exe, purché la proprietà `IsWebBootstrapper` sia attivata.  Verrà inoltre inserito nel manifesto dell'applicazione, se la proprietà `UpdateUrl` non è specificata.  
  
-   `SupportUrl` \(non visualizzata\) indica il percorso del collegamento relativo a un'applicazione inclusa nella finestra di dialogo **Installazione applicazioni**.  
  
 Di seguito sono riportate le proprietà disponibili nella finestra di dialogo **Aggiornamenti applicazione**, accessibile dalla scheda **Pubblica**.  
  
-   `UpdateEnabled` indica se l'applicazione deve verificare o meno la disponibilità di eventuali aggiornamenti.  
  
-   `UpdateMode` specifica se il controllo degli aggiornamenti deve essere eseguito o meno in background.  
  
-   `UpdateInterval` specifica la frequenza con cui l'applicazione deve verificare la disponibilità di eventuali aggiornamenti.  
  
-   `UpdateIntervalUnits` specifica se il valore di `UpdateInterval` è espresso in ore, giorni o settimane.  
  
-   `UpdateUrl` \(non visualizzata\) indica il percorso da cui l'applicazione riceverà gli aggiornamenti.  Se specificato, questo valore verrà inserito nel manifesto dell'applicazione.  
  
-   Di seguito sono riportate le proprietà disponibili nella finestra di dialogo **Opzioni di pubblicazione**, accessibile dalla scheda **Pubblica**.  
  
-   `PublisherName` specifica il nome dell'editore indicato nel messaggio visualizzato durante l'installazione o l'esecuzione dell'applicazione.  Nel caso di un'applicazione installata, viene inoltre utilizzato per specificare il nome della cartella nel menu Start.  
  
-   `ProductName` specifica il nome del prodotto indicato nel messaggio visualizzato durante l'installazione o l'esecuzione dell'applicazione.  Nel caso di un'applicazione installata, viene inoltre utilizzato per specificare il nome del collegamento nel menu Start.  
  
-   Di seguito sono riportate le proprietà disponibili nella finestra di dialogo **Prerequisiti**, accessibile dalla scheda **Pubblica**.  
  
-   `BootstrapperEnabled` determina se il programma di avvio automatico setup.exe deve essere generato.  
  
-   `IsWebBootstrapper` determina se il programma di avvio automatico setup.exe deve essere eseguito sul Web o in modalità basata su disco.  
  
## InstallURL, SupportUrl, PublishURL e UpdateURL  
 Nella tabella seguente vengono illustrate le quattro opzioni URL per la distribuzione ClickOnce.  
  
|Opzione URL|Descrizione|  
|-----------------|-----------------|  
|`PublishURL`|Richiesta se l'applicazione ClickOnce viene pubblicata su un sito Web.|  
|`InstallURL`|Parametro facoltativo.  Impostare questa opzione URL se il sito dell'installazione è diverso da `PublishURL`.  È possibile, ad esempio, impostare la proprietà `PublishURL` su un percorso FTP e la proprietà `InstallURL` su un URL Web.|  
|`SupportURL`|Parametro facoltativo.  Impostare questa opzione URL se il sito del supporto è diverso da `PublishURL`.  È possibile, ad esempio, impostare `SupportURL` sul sito Web del supporto tecnico clienti della società.|  
|`UpdateURL`|Parametro facoltativo.  Impostare questa opzione URL se il percorso di aggiornamento è diverso da `InstallURL`.  È possibile, ad esempio, impostare la proprietà `PublishURL` su un percorso FTP e la proprietà `UpdateURL` su un URL Web.|  
  
## Vedere anche  
 <xref:Microsoft.Build.Tasks.GenerateBootstrapper>   
 <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>   
 <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>   
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)