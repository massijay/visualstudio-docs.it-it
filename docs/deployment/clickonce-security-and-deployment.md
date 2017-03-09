---
title: "ClickOnce Security and Deployment | Microsoft Docs"
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
  - "Windows applications, ClickOnce deployment"
  - "deploying applications [ClickOnce]"
  - "ClickOnce deployment"
  - "publishing, ClickOnce"
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ClickOnce Security and Deployment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è una tecnologia di distribuzione che consente di creare applicazioni basate su Windows ad aggiornamento automatico che possono essere installate ed eseguite con un'interazione minima da parte dell'utente. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornisce un supporto completo per la pubblicazione e l'aggiornamento di applicazioni distribuite con la tecnologia ClickOnce, a condizione che i progetti siano stati sviluppati con Visual Basic e Visual C\#.  Per informazioni sulla distribuzione di applicazioni Visual C\+\+, vedere [Distribuzione ClickOnce per applicazioni Visual C\+\+](/visual-cpp/ide/clickonce-deployment-for-visual-cpp-applications).  
  
 La distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] risolve tre problemi principali della distribuzione:  
  
-   **Difficoltà di aggiornamento delle applicazioni.** Con la distribuzione tramite Microsoft Windows Installer, ogni volta che un'applicazione viene aggiornata, l'utente può installare un aggiornamento, sotto forma di file con estensione msp, e applicarlo al prodotto installato. La distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente invece di fornire gli aggiornamenti in modo automatico.  Vengono scaricate solo le parti dell'applicazione che sono state modificate e quindi l'applicazione completa aggiornata viene reinstallata da una nuova cartella affiancata.  
  
-   **Impatto sul computer dell'utente.** Con la distribuzione tramite Windows Installer le applicazioni sono spesso basate su componenti condivisi, con il conseguente rischio di conflitti di versione. Nella distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], invece, ciascuna applicazione è indipendente e non può interferire con le altre.  
  
-   **Autorizzazioni di sicurezza.** Nella distribuzione tramite Windows Installer sono necessarie autorizzazioni amministrative e agli utenti sono imposte limitazioni relative all'installazione. La distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente invece di eseguire l'installazione anche a utenti senza privilegi di amministratore, concedendo solo le autorizzazioni di sicurezza dall'accesso di codice necessarie per l'applicazione.  
  
 In passato, a causa di questi problemi, gli sviluppatori preferivano talvolta creare applicazioni Web anziché applicazioni basate su Windows, rinunciando a un'interfaccia utente avanzata a favore della semplicità di installazione.  La distribuzione di applicazioni mediante [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente di ottenere il meglio di entrambe le tecnologie.  
  
## Definizione di applicazione ClickOnce  
 Per applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] si intende qualsiasi applicazione Windows Presentation Foundation \(xbap\), Windows Form \(exe\), console \(exe\) o una soluzione Office \(dll\) pubblicata mediante la tecnologia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  È possibile pubblicare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in tre modi diversi: da una pagina Web, da una condivisione file di rete o da un supporto, ad esempio un CD\-ROM.  Un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può essere installata nel computer di un utente finale ed eseguita localmente anche quando il computer è offline, oppure può essere eseguita in modalità solo online senza essere installata in modo permanente nel computer dell'utente finale.  Per ulteriori informazioni, vedere [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] possono essere autoaggiornanti, ossia possono verificare la presenza di versioni più recenti non appena disponibili e sostituire automaticamente gli eventuali file aggiornati.  Lo sviluppatore può specificare il comportamento dell'aggiornamento e l'amministratore di rete può controllare anche le strategie di aggiornamento, ad esempio contrassegnando un aggiornamento come obbligatorio.  Sia l'utente finale che l'amministratore possono inoltre eseguire il ripristino di una versione precedente.  Per ulteriori informazioni, vedere [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Poiché le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono isolate, è impossibile che l'installazione o l'esecuzione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] interrompa le applicazioni esistenti.  Le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono autonome; ogni applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene installata in una cache per utente, per applicazione sicura e da questa eseguita.  Le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono eseguite nelle aree di sicurezza Intranet o Internet.  Se necessario, possono richiedere autorizzazioni di sicurezza elevate.  Per ulteriori informazioni, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
## Funzionamento della sicurezza ClickOnce  
 La sicurezza [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] principale è basata su certificati, criteri di sicurezza dall'accesso di codice e la richiesta di attendibilità ClickOnce.  
  
### Certificati  
 I certificati Authenticode sono utilizzati per verificare l'autenticità dell'editore dell'applicazione.  Tramite Authenticode per la distribuzione dell'applicazione, ClickOnce impedisce che un programma pericoloso figuri come programma legittimo proveniente da una fonte definita e attendibile.  Facoltativamente, i certificati possono essere utilizzati anche per firmare l'applicazione e i manifesti della distribuzione al fine di dimostrare che i file non sono stati alterati.  Per ulteriori informazioni, vedere [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md).  I certificati possono inoltre essere utilizzati per configurare i computer client in modo che dispongano di un elenco di editori attendibili.  Se un'applicazione proviene da un editore attendibile, può essere installata senza alcuna interazione da parte dell'utente.  Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
### Sicurezza per l'accesso al codice  
 La sicurezza dall'accesso di codice consente di limitare l'accesso alle risorse protette da parte del codice.  Nella maggior parte dei casi, è possibile scegliere le aree Internet o Intranet locale per limitare le autorizzazioni.  Utilizzare la pagina **Sicurezza** in **Progettazione  progetti** per richiedere l'area adatta per l'applicazione.  È inoltre possibile eseguire il debug di applicazioni con autorizzazioni limitate per emulare l'esperienza dell'utente finale.  Per ulteriori informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
### Richiesta di attendibilità ClickOnce  
 Se l'applicazione richiede più autorizzazioni di quante ne consenta l'area, è possibile che venga richiesto all'utente finale di stabilirne l'attendibilità.  L'utente finale può decidere se applicazioni ClickOnce quali le applicazioni Windows Form, le applicazioni Windows Presentation Foundation, le applicazioni console, le applicazioni browser XAML e le soluzioni Office siano da considerarsi attendibili ai fini dell'esecuzione.  Per ulteriori informazioni, vedere [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).  
  
## Modalità di funzionamento della distribuzione ClickOnce  
 L'architettura principale di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è basata su due file manifesto XML: un manifesto dell'applicazione e uno di distribuzione.  I file sono utilizzati per descrivere il percorso dal quale vengono installate le applicazioni ClickOnce, il modo e il momento in cui vengono aggiornate.  
  
### Pubblicazione di applicazioni ClickOnce  
 Nel manifesto dell'applicazione viene descritta l'applicazione vera e propria,  inclusi gli assembly, le dipendenze e i file da cui è costituita, oltre alle autorizzazioni necessarie e al percorso in cui saranno disponibili gli aggiornamenti.  Il manifesto dell'applicazione viene creato dallo sviluppatore mediante la Pubblicazione guidata di Visual Studio o lo strumento per la generazione e la modifica di manifesti \(Mage.exe\) di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Per ulteriori informazioni, vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
 Nel manifesto di distribuzione viene descritta la distribuzione dell'applicazione.  Sono inclusi il percorso del manifesto dell'applicazione e la versione dell'applicazione da eseguire nei client.  
  
### Distribuzione delle applicazioni ClickOnce  
 Una volta creato, il manifesto di distribuzione viene copiato nel percorso di distribuzione,  che può essere un server Web, una condivisione file di rete o un supporto quale un CD.  Anche il manifesto dell'applicazione e tutti i file dell'applicazione vengono copiati nel percorso specificato nel manifesto di distribuzione,  che può corrispondere al percorso di distribuzione o può essere un percorso differente.  In caso di utilizzo della **Pubblicazione guidata** di Visual Studio, le operazioni di copia vengono eseguite automaticamente.  
  
### Installazione di applicazioni ClickOnce  
 Dopo la distribuzione nell'apposito percorso, gli utenti finali possono scaricare e installare l'applicazione facendo clic su un'icona che rappresenta il file del manifesto di distribuzione su una pagina Web o in una cartella.  Nella maggior parte dei casi viene visualizzata una semplice finestra di dialogo di conferma, dopodichè l'installazione prosegue e l'applicazione viene avviata senza altri interventi da parte dell'utente.  Nei casi in cui l'applicazione richiede autorizzazioni elevate, o se l'applicazione non è firmata con un certificato attendibile, viene richiesto all'utente di concedere l'autorizzazione prima di proseguire con l'installazione.  Sebbene le installazioni ClickOnce siano per utente, in presenza di prerequisiti che richiedono privilegi di amministratore potrebbe essere necessaria l'elevazione dell'autorizzazione.  Per ulteriori informazioni sulle autorizzazioni elevate, vedere [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md).  
  
 I certificati possono essere considerati attendibili a livello di computer o di impresa, così da consentire l'installazione senza alcuna notifica delle applicazioni ClickOnce firmate con un certificato attendibile.  Per ulteriori informazioni sui certificati attendibili, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
 L'applicazione può essere aggiunta al menu **Start** dell'utente e al gruppo **Installazione applicazioni** nel **Pannello di controllo**.  A differenza di altre tecnologie di distribuzione, non viene aggiunto alcun elemento nella cartella **Programmi** né nel Registro di sistema e non sono richiesti diritti amministrativi per l'installazione.  
  
> [!NOTE]
>  È inoltre possibile impedire che l'applicazione venga aggiunta al **menu Start** e al gruppo **Installazione applicazioni**, esattamente come per un'applicazione Web.  Per ulteriori informazioni, vedere [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
### Aggiornamento di applicazioni ClickOnce  
 Quando gli sviluppatori creano una versione aggiornata dell'applicazione, generano un nuovo manifesto dell'applicazione e copiano i file in un percorso di distribuzione, che in genere corrisponde a una cartella di pari livello della cartella di distribuzione dell'applicazione originale.  L'amministratore aggiorna il manifesto di distribuzione in modo da puntare al percorso della nuova versione dell'applicazione.  
  
> [!NOTE]
>  Per l'esecuzione di queste operazioni è possibile utilizzare la **Pubblicazione guidata** di Visual Studio.  
  
 In aggiunta al percorso di distribuzione, il manifesto di distribuzione contiene anche un percorso di aggiornamento \(una pagina Web o una condivisione di file della rete\) dove l'applicazione verifica la presenza di versioni aggiornate.  Le proprietà **Publish** di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono utilizzate per specificare quando e con quale frequenza l'applicazione deve verificare la disponibilità di eventuali aggiornamenti.  È possibile specificare il comportamento dell'aggiornamento nel manifesto di distribuzione oppure presentare una serie di opzioni nell'interfaccia utente dell'applicazione mediante le API di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Le proprietà relative alla pubblicazione possono inoltre essere utilizzate per rendere obbligatori gli aggiornamenti o per eseguire il rollback a una versione precedente.  Per ulteriori informazioni, vedere [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
### Programmi di installazione di terze parti  
 È possibile personalizzare il programma di installazione ClickOnce per installare componenti di terze parti insieme all'applicazione.  È necessario disporre del package ridistribuibile \(file EXE o MSI\) e descriverlo con un manifesto del prodotto indipendente dalla lingua e un manifesto di pacchetto specifico della lingua.  Per ulteriori informazioni, vedere [Creazione di programmi di avvio automatico](../deployment/creating-bootstrapper-packages.md).  
  
## Strumenti ClickOnce  
 Nella tabella seguente vengono illustrati gli strumenti che è possibile utilizzare per generare, modificare, firmare e rifirmare i manifesti dell'applicazione e della distribuzione.  
  
|Strumento|Descrizione|  
|---------------|-----------------|  
|[Pagina Sicurezza, Progettazione progetti](../ide/reference/security-page-project-designer.md)|Consente di firmare i manifesti dell'applicazione e della distribuzione.|  
|[Pagina Pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md)|Consente di generare e modificare i manifesti dell'applicazione e della distribuzione per applicazioni Visual Basic e Visual C\#.|  
|[Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)|Consente di generare i manifesti dell'applicazione e della distribuzione per applicazioni Visual Basic, Visual C\# e Visual C\+\+.<br /><br /> Consente di firmare e rifirmare i manifesti dell'applicazione e della distribuzione.<br /><br /> Può essere eseguito da script batch e dal prompt dei comandi.|  
|[MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)|Consente di generare e modificare i manifesti dell'applicazione e della distribuzione.<br /><br /> Consente di firmare e rifirmare i manifesti dell'applicazione e della distribuzione.|  
|[GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md)|Consente di generare il manifesto dell'applicazione.<br /><br /> Può essere eseguito da MSBuild.  Per ulteriori informazioni, vedere [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|[GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)|Consente di generare il manifesto della distribuzione.<br /><br /> Può essere eseguito da MSBuild.  Per ulteriori informazioni, vedere [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|[SignFile Task](../msbuild/signfile-task.md)|Consente di firmare i manifesti dell'applicazione e della distribuzione.<br /><br /> Può essere eseguito da MSBuild.  Per ulteriori informazioni, vedere [MSBuild Reference](../msbuild/msbuild-reference.md).|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|Consente di sviluppare un'applicazione personalizzata per generare i manifesti dell'applicazione e della distribuzione.|  
  
 Nella tabella seguente viene indicata la versione di .NET Framework richiesta dai vari browser per supportare le applicazioni ClickOnce.  
  
|Browser|Versione di .NET Framework|  
|-------------|--------------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## Vedere anche  
 [ClickOnce Deployment on Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Deploying COM Components with ClickOnce](../deployment/deploying-com-components-with-clickonce.md)   
 [Building ClickOnce Applications from the Command Line](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [Debugging ClickOnce Applications That Use System.Deployment.Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)