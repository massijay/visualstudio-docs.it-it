---
title: "Walkthrough: Manually Deploying a ClickOnce Application | Microsoft Docs"
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
  - "Mage.exe, manual ClickOnce deployments"
  - "MageUI.exe, manual ClickOnce deployments"
  - "deploying applications [ClickOnce], manual ClickOnce deployments"
  - "ClickOnce deployment, manually"
  - "ClickOnce deployment, SDK tools"
  - "manual ClickOnce deployments"
  - "manifests [ClickOnce]"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manually Deploying a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se non è possibile utilizzare Visual Studio per distribuire l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o è necessario utilizzare funzionalità di distribuzione avanzate, ad esempio la distribuzione di applicazioni attendibili, è consigliabile utilizzare lo strumento della riga di comando Mage.exe per la creazione dei manifesti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  In questa procedura dettagliata viene descritto come creare una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilizzando la versione per riga di comando \(Mage.exe\) o la versione con interfaccia grafica \(MageUI.exe\) dello strumento per la generazione e la modifica di manifesti.  
  
## Prerequisiti  
 Questa procedura dettagliata presenta alcuni prerequisiti e opzioni che è necessario scegliere prima di compilare una distribuzione.  
  
-   Installare Mage.exe e MageUI.exe.  
  
     Mage.exe e MageUI.exe fanno parte di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  È necessario avere installato [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] oppure disporre della versione di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] inclusa in Visual Studio.  Per ulteriori informazioni, vedere [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) su MSDN.  
  
-   Fornire un'applicazione da distribuire.  
  
     In questa procedura dettagliata si presuppone che si disponga di un'applicazione Windows pronta per la distribuzione.  Tale applicazione verrà indicata come AppToDeploy.  
  
-   Determinare come verrà distribuita la distribuzione.  
  
     La distribuzione può essere eseguita mediante Web, condivisione file o CD.  Per ulteriori informazioni, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
-   Determinare se l'applicazione richiede un livello di attendibilità elevato.  
  
     Se per l'applicazione è necessario un livello di attendibilità totale, ad esempio l'accesso completo al sistema dell'utente, è possibile definire questa impostazione mediante l'opzione `-TrustLevel` di Mage.exe.  Se si desidera definire un set di autorizzazioni personalizzato per l'applicazione, è possibile copiare la sezione relativa alle autorizzazioni Internet o Intranet da un altro manifesto, modificarla in base alle proprie esigenze, quindi aggiungerla al manifesto dell'applicazione utilizzando un editor di testo o lo strumento MageUI.exe.  Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
-   Ottenere un certificato Authenticode.  
  
     È consigliabile firmare la distribuzione con un certificato Authenticode.  È possibile generare un certificato di prova utilizzando Visual Studio, MageUI.exe o gli strumenti MakeCert.exe e Pvk2Pfx.exe oppure è possibile ottenere un certificato da un'Autorità di certificazione \(CA\).  Se si sceglie di utilizzare la distribuzione di applicazioni attendibili, è necessario eseguire anche un'installazione unica del certificato in tutti i computer client.  Per ulteriori informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md).  
  
-   Verificare che l'applicazione non disponga di un manifesto con informazioni di Controllo dell'account utente.  
  
     È necessario determinare se l'applicazione contiene un manifesto con informazioni di Controllo dell'account utente, quale un elemento `<dependentAssembly>`.  Per esaminare un manifesto di applicazione, è possibile utilizzare l'utilità [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) di Windows Sysinternals.  
  
     Se l'applicazione contiene un manifesto con dettagli di Controllo dell'account utente, è necessario ricompilarla senza tali informazioni.  Per un progetto C\# in Visual Studio, aprire le proprietà del progetto e selezionare la scheda Applicazione.  Nell'elenco a discesa **Manifesto** selezionare **Crea applicazione senza manifesto**.  Per un progetto di Visual Basic in Visual Studio, aprire le proprietà del progetto, selezionare la scheda Applicazione e fare clic su **Visualizza impostazioni di controllo dell'account utente**.  Nel file del manifesto aperto rimuovere tutti gli elementi all'interno del solo elemento `<asmv1:assembly>`.  
  
-   Determinare se l'applicazione richiede prerequisiti nel computer client.  
  
     Le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuite da Visual Studio possono includere un programma di avvio automatico di installazione dei prerequisiti \(setup.exe\) con la distribuzione.  In questa procedura dettagliata vengono creati i due manifesti necessari per una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  È possibile creare un programma di avvio automatico dei prerequisiti utilizzando l'[GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md).  
  
### Per distribuire un'applicazione mediante lo strumento della riga di comando Mage.exe  
  
1.  Creare una directory dove si archivieranno i file della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Nella directory di distribuzione creata creare una sottodirectory della versione.  Se l'applicazione viene distribuita per la prima volta, denominare la sottodirectory della versione 1.0.0.0.  
  
    > [!NOTE]
    >  La versione della distribuzione può essere distinta da quella dell'applicazione.  
  
3.  Copiare tutti i file dell'applicazione, inclusi eseguibili, assembly, risorse e file di dati, nella sottodirectory della versione.  Se necessario, è possibile creare ulteriori sottodirectory contenenti file aggiuntivi.  
  
4.  Aprire [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] o il prompt dei comandi di Visual Studio e passare alla sottodirectory della versione.  
  
5.  Creare il manifesto dell'applicazione eseguendo una chiamata a Mage.exe.  Con l'istruzione seguente viene creato un manifesto dell'applicazione per il codice compilato da eseguire nel processore Intel x86.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Assicurarsi di includere il punto \(.\) dopo l'opzione `-FromDirectory`, che indica la directory corrente.  Se non si include il punto, è necessario specificare il percorso ai file dell'applicazione.  
  
6.  Firmare il manifesto dell'applicazione con il certificato Authenticode.  Sostituire *mycert.pfx* con il percorso al file del certificato.  Sostituire *passwd* con la password per il file del certificato.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  Sostituire la radice della directory di distribuzione.  
  
8.  Generare il manifesto di distribuzione eseguendo una chiamata a Mage.exe.  Per impostazione predefinita, Mage.exe contrassegna la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] come un'applicazione installata, consentendone l'esecuzione sia online che offline.  Per rendere disponibile l'applicazione solo quando l'utente è online, utilizzare l'opzione `-Install` con il valore `false`.  Se si utilizza l'impostazione predefinita e gli utenti installeranno l'applicazione da un sito Web o da una condivisione file, assicurarsi che il valore dell'opzione `-ProviderUrl` punti al percorso del manifesto dell'applicazione sul server Web o sulla condivisione.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Firmare il manifesto della distribuzione con il certificato Authenticode.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Copiare tutti i file della directory di distribuzione sul supporto o nella destinazione di distribuzione.  Questo percorso può corrispondere a una cartella su un sito Web o FTP, a una condivisione file o a un CD\-ROM.  
  
11. Fornire agli utenti l'URL, l'UNC o il supporto fisico necessario per l'installazione dell'applicazione.  Nel caso di un URL o UNC, è necessario indicare agli utenti il percorso completo del manifesto della distribuzione.  Ad esempio, se AppToDeploy viene distribuita su http:\/\/webserver01\/, nella directory AppToDeploy, il percorso URL completo sarà http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
### Per distribuire un'applicazione mediante lo strumento con interfaccia grafica MageUI.exe  
  
1.  Creare una directory dove si archivieranno i file della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Nella directory di distribuzione creata creare una sottodirectory della versione.  Se l'applicazione viene distribuita per la prima volta, denominare la sottodirectory della versione 1.0.0.0.  
  
    > [!NOTE]
    >  La versione della distribuzione è probabilmente distinta da quella dell'applicazione.  
  
3.  Copiare tutti i file dell'applicazione, inclusi eseguibili, assembly, risorse e file di dati, nella sottodirectory della versione.  Se necessario, è possibile creare ulteriori sottodirectory contenenti file aggiuntivi.  
  
4.  Avviare lo strumento grafico MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Creare un nuovo manifesto dell'applicazione scegliendo **Nuovo** dal menu **File**, quindi **Manifesto applicazione**.  
  
6.  Nella scheda **Nome** predefinita digitare il nome e il numero di versione della distribuzione.  Specificare inoltre un valore nel campo **Processore** per il quale l'applicazione viene compilata, ad esempio x86.  
  
7.  Selezionare la scheda **File** e quindi fare clic sul pulsante con i puntini di sospensione \(**...**\) accanto alla casella di testo **Directory applicazione**.  Verrà visualizzata la finestra di dialogo Sfoglia per cartelle.  
  
8.  Selezionare la sottodirectory della versione contenente i file dell'applicazione, quindi fare clic su **OK**.  
  
9. Se si eseguirà la distribuzione da Internet Information Services \(IIS\), selezionare la casella di controllo **Durante la popolazione aggiungi l'estensione .deploy a qualsiasi file ne sia sprovvisto**.  
  
10. Scegliere il pulsante **Popola** per aggiungere tutti i file dell'applicazione all'elenco dei file.  Se l'applicazione contiene più file eseguibili, contrassegnare quello principale per la distribuzione corrente come applicazione di avvio selezionando **Punto di ingresso** dall'elenco a discesa **Tipo file**.  Se l'applicazione contiene un solo file eseguibile, questo verrà contrassegnato automaticamente da MageUI.exe.  
  
11. Fare clic sulla scheda **Autorizzazioni necessarie** e selezionare il livello di attendibilità che dovrà essere richiesto dall'applicazione.  Il valore predefinito, **FullTrust**, è adatto alla maggior parte delle applicazioni.  
  
12. Scegliere **File**, **Salva con nome** dal menu.  Verrà visualizzata la finestra di dialogo Opzioni di firma con la richiesta di firmare il manifesto dell'applicazione.  
  
13. Se si dispone di un certificato archiviato come file nel file system, utilizzare l'opzione **Firma con file di certificato** e selezionare il certificato dal file system utilizzando il pulsante con i puntini di sospensione \(**...**\).  Digitare quindi la password del certificato.  
  
     In alternativa  
  
     Se il certificato si trova in un archivio certificati accessibile dal computer locale, scegliere l'opzione **Firma con certificato archiviato** e selezionare il certificato dall'elenco fornito.  
  
14. Fare clic su **OK** per firmare il manifesto dell'applicazione.  Verrà visualizzata la finestra di dialogo Salva con nome.  
  
15. Nella finestra di dialogo Salva con nome specificare la directory della versione, quindi fare clic su **Salva**.  
  
16. Scegliere **File**, **Nuovo**, **Manifesto di distribuzione** dal menu per creare il manifesto della distribuzione.  
  
17. Nella scheda **Nome** specificare un nome e un numero di versione per questa distribuzione \(1.0.0.0 in questo esempio\).  Specificare inoltre un valore nel campo **Processore** per il quale l'applicazione viene compilata, ad esempio x86.  
  
18. Fare clic sulla scheda **Descrizione** e specificare i valori per **Editore** e **Prodotto**.  **Prodotto** è il nome assegnato all'applicazione nel menu Start di Windows quando l'applicazione viene installata in un computer client per l'utilizzo offline.  
  
19. Selezionare la scheda **Opzioni di distribuzione** e nella casella di testo **Percorso iniziale** specificare il percorso del manifesto dell'applicazione nel server Web o nella condivisione.  Ad esempio, \\\\myServer\\myShare\\AppToDeploy.application.  
  
20. Se in un passaggio precedente è stata aggiunta l'estensione deploy, selezionare anche **Usa l'estensione di file .deploy**.  
  
21. Fare clic sulla scheda **Opzioni aggiornamento** e specificare la frequenza di aggiornamento che si desidera impostare per l'applicazione.  Se l'applicazione utilizza <xref:System.Deployment.Application.UpdateCheckInfo> per il controllo automatico degli aggiornamenti, deselezionare la casella di controllo **Controlla aggiornamenti dell'applicazione**.  
  
22. Fare clic sulla scheda **Riferimento all'applicazione**, quindi fare clic sul pulsante **Seleziona manifesto**.  Verrà visualizzata la finestra di dialogo Apri.  
  
23. Selezionare il manifesto dell'applicazione creato in precedenza, quindi fare clic su **Apri**.  
  
24. Scegliere **File**, **Salva con nome** dal menu.  Verrà visualizzata la finestra di dialogo Opzioni di firma con la richiesta di firmare il manifesto della distribuzione.  
  
25. Se si dispone di un certificato archiviato come file nel file system, utilizzare l'opzione **Firma con file di certificato** e selezionare il certificato dal file system utilizzando il pulsante con i puntini di sospensione \(**...**\).  Digitare quindi la password del certificato.  
  
     In alternativa  
  
     Se il certificato si trova in un archivio certificati accessibile dal computer locale, scegliere l'opzione **Firma con certificato archiviato** e selezionare il certificato dall'elenco fornito.  
  
26. Fare clic su **OK** per firmare il manifesto della distribuzione.  Verrà visualizzata la finestra di dialogo Salva con nome.  
  
27. Nella finestra di dialogo **Salva con nome** risalire di una directory verso la radice della distribuzione, quindi fare clic su **Salva**.  
  
28. Copiare tutti i file della directory di distribuzione sul supporto o nella destinazione di distribuzione.  Questo percorso può corrispondere a una cartella su un sito Web o FTP, a una condivisione file o a un CD\-ROM.  
  
29. Fornire agli utenti l'URL, l'UNC o il supporto fisico necessario per l'installazione dell'applicazione.  Nel caso di un URL o UNC, è necessario indicare agli utenti il percorso completo del manifesto della distribuzione.  Ad esempio, se AppToDeploy viene distribuita su http:\/\/webserver01\/, nella directory AppToDeploy, il percorso URL completo sarà http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
## Passaggi successivi  
 Quando è necessario distribuire una nuova versione dell'applicazione, creare una nuova directory con il nome della nuova versione, ad esempio 1.0.0.1, quindi copiare i nuovi file dell'applicazione nella nuova directory.  È quindi necessario seguire i passaggi precedenti per creare e firmare un nuovo manifesto dell'applicazione e aggiornare e firmare il manifesto della distribuzione.  Assicurarsi di specificare la stessa versione superiore nelle chiamate a `-New` e a `–Update` di Mage.exe, in quanto [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aggiorna solo le versioni superiori, con il numero intero all'estrema sinistra più significativo.  Se è stato utilizzato MageUI.exe, è possibile aggiornare il manifesto della distribuzione aprendolo, facendo clic sulla scheda **Riferimento all'applicazione**, facendo clic sul pulsante **Seleziona manifesto**, quindi selezionando il manifesto dell'applicazione aggiornato.  
  
## Vedere anche  
 [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)