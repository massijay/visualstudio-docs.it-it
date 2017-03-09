---
title: "Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re-Signing and that Preserves Branding Information | Microsoft Docs"
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
  - "branding"
  - "preserved branding information"
  - "ClickOnce deployment, manually"
  - "multiple ClickOnce deployment and branding"
  - "ClickOnce deployment, SDK tools"
  - "customer deployments"
  - "manual ClickOnce deployments"
  - "manifests [ClickOnce]"
  - "ClickOnce applications, deployed by others"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re-Signing and that Preserves Branding Information
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si crea un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e quindi la si passa a un cliente per la pubblicazione e la distribuzione, in genere il cliente deve aggiornare il manifesto della distribuzione e firmarlo di nuovo. Sebbene questo sia ancora il metodo consigliato nella maggior parte dei casi, in .NET Framework 3.5 è possibile di creare distribuzioni di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] che possono essere distribuite dai clienti senza dover rigenerare un nuovo manifesto della distribuzione.  Per ulteriori informazioni, vedere [Deploying ClickOnce Applications For Testing and Production Servers without Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Quando si crea un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per poi passarla a un cliente che la pubblicherà e distribuirà, l'applicazione può utilizzare le informazioni di personalizzazione del cliente oppure conservare le proprie.  Se, ad esempio, l'applicazione è una singola applicazione proprietaria, è possibile che si desideri conservare le proprie informazioni di personalizzazione.  Se invece l'applicazione è fortemente personalizzata per ciascun cliente, è possibile che si desideri utilizzare le informazioni di personalizzazione del cliente.  .NET Framework 3.5 consente di conservare le informazioni di personalizzazione, le informazioni sull'editore nonché la firma di sicurezza quando si affida un'applicazione a un'organizzazione per la distribuzione.  Per ulteriori informazioni, vedere [Creating ClickOnce Applications for Others to Deploy](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  In questa procedura dettagliata le distribuzioni vengono create manualmente utilizzando lo strumento della riga di comando Mage.exe o lo strumento grafico MageUI.exe.  Per ulteriori informazioni sulle distribuzioni manuali, vedere [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Prerequisiti  
 Per eseguire i passaggi della procedura, è necessario disporre di quanto segue:  
  
-   Un'applicazione Windows Form pronta per la distribuzione.  Tale applicazione verrà indicata come WindowsFormsApp1.  
  
-   Visual Studio o Windows SDK.  
  
### Per distribuire un'applicazione ClickOnce con il supporto per più distribuzioni e marchi utilizzando Mage.exe  
  
1.  Aprire un prompt dei comandi di Visual Studio o di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] e passare alla directory in cui verranno archiviati i file di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Creare una directory con il nome corrispondente alla versione corrente della distribuzione.  Se l'applicazione viene distribuita per la prima volta, il nome più probabile sarà 1.0.0.0.  
  
    > [!NOTE]
    >  La versione della distribuzione può essere distinta da quella dei file dell'applicazione.  
  
3.  Creare una sottodirectory con il nome bin e copiarvi tutti i file dell'applicazione, inclusi eseguibili, assembly, risorse e file di dati.  
  
4.  Generare il manifesto dell'applicazione eseguendo una chiamata a Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Firmare il manifesto dell'applicazione con il certificato digitale.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generare il manifesto di distribuzione eseguendo una chiamata a Mage.exe.  Per impostazione predefinita, Mage.exe contrassegna la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] come un'applicazione installata, consentendone l'esecuzione sia online che offline.  Per rendere disponibile l'applicazione solo quando l'utente è online, utilizzare l'argomento `-i` con il valore `f`.  Poiché questa applicazione usufruisce della funzionalità di distribuzione multipla, escludere l'argomento `-providerUrl` di Mage.exe.  \(Nelle versioni di .NET Framework precedenti alla versione 3.5, l'esclusione di `-providerUrl` per un'applicazione offline restituisce un errore.\)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Non firmare il manifesto di distribuzione.  
  
8.  Fornire tutti i file al cliente che distribuirà l'applicazione nella propria rete.  
  
9. In questa fase, il cliente deve firmare il manifesto di distribuzione con il proprio certificato autogenerato.  Se, ad esempio, il cliente lavora per un'azienda denominata Adventure Works, può generare un certificato autofirmato utilizzando lo strumento MakeCert.exe.  Successivamente, dovrà utilizzare lo strumento Pvk2pfx.exe per combinare i file creati da MakeCert.exe in un file PFX che è possibile passare a Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Il cliente utilizza quindi questo certificato per firmare il manifesto di distribuzione.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Il cliente distribuisce l'applicazione ai propri utenti.  
  
### Per distribuire un'applicazione ClickOnce con il supporto per più distribuzioni e marchi utilizzando MageUI.exe  
  
1.  Aprire un prompt dei comandi di Visual Studio o di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] e passare alla directory in cui verranno archiviati i file di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
2.  Creare una sottodirectory con il nome bin e copiarvi tutti i file dell'applicazione, inclusi eseguibili, assembly, risorse e file di dati.  
  
3.  Creare una sottodirectory con il nome corrispondente alla versione corrente della distribuzione.  Se l'applicazione viene distribuita per la prima volta, il nome più probabile sarà 1.0.0.0.  
  
    > [!NOTE]
    >  La versione della distribuzione può essere distinta da quella dei file dell'applicazione.  
  
4.  Spostare la directory \\bin in quella creata al passaggio 2.  
  
5.  Avviare lo strumento grafico MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Creare un nuovo manifesto dell'applicazione scegliendo **Nuovo** dal menu **File**, quindi **Manifesto applicazione**.  
  
7.  Nella scheda **Nome** predefinita immettere il nome e il numero di versione della distribuzione.  Specificare inoltre un valore per l'opzione **Editore** che verrà utilizzato come nome di cartella per il collegamento dell'applicazione nel menu Start al momento della distribuzione.  
  
8.  Selezionare la scheda **Opzioni applicazione** e fare clic su **Usa manifesto applicazione per informazioni sull'attendibilità**.  In questo modo si attiverà il marchio di terze parti per questa applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
9. Fare clic sulla scheda **File**, quindi scegliere il pulsante **Sfoglia** accanto alla casella di testo Directory dell'applicazione.  
  
10. Selezionare la directory contenente i file dell'applicazione creati nel passaggio 2, quindi scegliere **OK** nella finestra di dialogo per la selezione delle cartelle.  
  
11. Scegliere il pulsante **Popola** per aggiungere tutti i file dell'applicazione all'elenco dei file.  Se l'applicazione contiene più file eseguibili, contrassegnare quello principale per la distribuzione corrente come applicazione di avvio selezionando **Punto di ingresso** dall'elenco a discesa **Tipo file**.  Se l'applicazione contiene un solo file eseguibile, questo verrà contrassegnato automaticamente da MageUI.exe.  
  
12. Fare clic sulla scheda **Autorizzazioni necessarie** e selezionare il livello di attendibilità che dovrà essere richiesto dall'applicazione.  Il valore predefinito, **Attendibilità totale**, è adatto alla maggior parte delle applicazioni.  
  
13. Scegliere **Salva** dal menu **File**, quindi salvare il manifesto dell'applicazione.  Al momento del salvataggio del manifesto verrà chiesto di firmarlo.  
  
14. Se si dispone di un certificato archiviato nel file system, utilizzare l'opzione **Firma come file di certificato** e selezionare il certificato dal file system utilizzando il pulsante con i puntini di sospensione \(**...**\).  
  
     In alternativa  
  
     Se il certificato si trova in un archivio certificati accessibile dal computer locale, scegliere l'opzione **Firma con un certificato archiviato** e selezionare il certificato dall'elenco fornito.  
  
15. Scegliere **Nuovo** dal menu **File**, quindi **Manifesto di distribuzione** per creare il manifesto di distribuzione. Nella scheda **Nome** specificare un nome e un numero di versione \(in questo esempio, 1.0.0.0\).  
  
16. Fare clic sulla scheda **Aggiorna** e specificare la frequenza di aggiornamento che si desidera impostare per l'applicazione.  Se l'applicazione utilizza l'API della distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per il controllo automatico degli aggiornamenti, deselezionare la casella di controllo **Controlla aggiornamenti dell'applicazione**.  
  
17. Fare clic sulla scheda **Riferimenti applicazione**.  Tutti i valori di questa scheda possono essere impostati automaticamente scegliendo il pulsante **Seleziona manifesto** e selezionando il manifesto dell'applicazione creato nei passaggi precedenti.  
  
18. Scegliere **Salva** e salvare il manifesto di distribuzione sul disco.  Al momento del salvataggio del manifesto verrà chiesto di firmarlo.  Fare clic su **Annulla** per salvare il manifesto senza firmarlo.  
  
19. Fornire tutti i file dell'applicazione al cliente.  
  
20. In questa fase, il cliente deve firmare il manifesto di distribuzione con il proprio certificato autogenerato.  Se, ad esempio, il cliente lavora per un'azienda denominata Adventure Works, può generare un certificato autofirmato utilizzando lo strumento MakeCert.exe.  Successivamente, dovrà utilizzare lo strumento Pvk2pfx.exe per combinare i file creati da MakeCert.exe in un file PFX che è possibile passare a MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Dopo aver generato il certificato, il cliente firma il manifesto di distribuzione aprendolo in MageUI.exe e quindi salvandolo.  Quando la finestra di dialogo di firma viene visualizzata, il cliente seleziona l'opzione **Firma come file di certificato** e sceglie il file PFX che ha salvato su disco.  
  
22. Il cliente distribuisce l'applicazione ai propri utenti.  
  
## Passaggi successivi  
  
## Vedere anche  
 [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)