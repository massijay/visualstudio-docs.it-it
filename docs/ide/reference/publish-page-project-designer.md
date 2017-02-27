---
title: "Pagina Pubblica, Progettazione progetti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Creazione progetti, pagina Pubblica"
  - "Pagina Pubblica in Creazione progetti"
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Pagina Pubblica, Progettazione progetti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina **Pubblica** della **Creazione progetti** consente di configurare le proprietà relative alla distribuzione ClickOnce.  
  
 Per accedere alla pagina **Pubblica**, selezionare un nodo di progetto in **Esplora soluzioni**, quindi fare clic su **Proprietà** dal menu **Progetto**. In **Progettazione progetti** fare clic sulla scheda **Pubblica**.  
  
> [!NOTE]
>  Alcune delle proprietà ClickOnce descritte qui possono essere impostate anche nella **Pubblicazioneguidata**, disponibile nel menu **Compila** oppure facendo clic sul pulsante **Pubblicazioneguidata** in questa pagina.  
  
## Elenco UIElement  
 **Posizione cartella di pubblicazione**  
 Specifica il percorso in cui l'applicazione viene pubblicata. Può essere un percorso di unità \(`C:\deploy\myapplication`\), una condivisione file \(`\\server\myapplication`\), un server FTP \(`ftp://ftp.microsoft.com/myapplication`\) o un sito Web \(`http://www.microsoft.com/myapplication`\). Si noti che il testo deve essere presente nella scheda **Posizione di pubblicazione** perché il pulsante Sfoglia \(**...**\) funzioni.  
  
 Per impostazione predefinita, il percorso di pubblicazione è `http://localhost/<projectname>/` se IIS è installato o la directory `publish\` se IIS non è installato. Se il computer esegue Windows Vista, il valore predefinito è sempre la directory `publish\`, indipendentemente dal fatto che sia installato IIS.  
  
 **URL cartella di installazione**  
 Facoltativo. Specifica un sito Web a cui gli utenti accedono per installare l'applicazione. Questa operazione è necessaria solo se si tratta di un percorso diverso da **Posizione di pubblicazione**, ad esempio quando l'applicazione viene pubblicata in un server di gestione temporanea.  
  
 **Modalità di installazione e impostazioni**  
 Determina se l'applicazione viene eseguita direttamente dalla **Posizione di pubblicazione** \(quando è selezionata l'opzione **Applicazione disponibile solo online**\) o viene installata e aggiunta al menu **Start** e all'elemento **Installazione applicazioni** del **Pannello di controllo** \(quando è selezionata l'opzione **Applicazione disponibile anche offline**\).  
  
 Per le applicazioni Web Browser WPF, l'opzione **Applicazione disponibile anche offline** è disabilitata, perché tali applicazioni sono disponibili solo online.  
  
 **File applicazione**  
 Apre [Application Files Dialog Box](http://msdn.microsoft.com/it-it/b06dff3a-b87a-4caf-996b-7a4acf8137a8) che consente di specificare come e dove vengono installati i singoli file.  
  
 **Prerequisiti**  
 Apre il [Finestra di dialogo Prerequisiti](../../ide/reference/prerequisites-dialog-box.md) che consente di specificare i componenti necessari, ad esempio .NET Framework, da installare insieme all'applicazione.  
  
 **Aggiornamenti**  
 Apre [Application Updates Dialog Box](http://msdn.microsoft.com/it-it/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f) che consente di specificare il comportamento di aggiornamento per l'applicazione. Non è disponibile quando è selezionata l'opzione **Applicazione disponibile solo online**.  
  
 **Opzioni**  
 Apre [Publish Options Dialog Box](http://msdn.microsoft.com/it-it/fd9baa1b-7311-4f9e-8ffb-ae50cf110592) che consente di specificare altre opzioni di pubblicazione avanzate.  
  
 **Versione di pubblicazione**  
 Imposta il numero della versione di pubblicazione per l'applicazione. Quando viene modificato il numero di versione, l'applicazione viene pubblicata come aggiornamento. Ogni parte della versione di pubblicazione \(**Principale**, **Secondaria**, **Compilazione**, **Revisione**\) può avere un valore massimo di 65355 \(<xref:System.UInt16.MaxValue>\), il massimo consentito da <xref:System.Version>.  
  
 Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
 **Incrementa automaticamente revisione a ogni pubblicazione**  
 Facoltativo. Quando questa opzione è selezionata \(impostazione predefinita\), la parte **Revisione** del numero di versione viene incrementata di un'unità ogni volta che viene pubblicata l'applicazione. In questo modo l'applicazione viene pubblicata come aggiornamento.  
  
 **Pubblicazione guidata**  
 Apre [Publish Wizard](http://msdn.microsoft.com/it-it/fc6abebd-13d6-48e4-a567-fbc52dad0872). Il completamento della Pubblicazione guidata ha lo stesso effetto dell'esecuzione del comando **Pubblica** del menu **Compila**.  
  
 **Pubblica**  
 Pubblica l'applicazione usando le impostazioni correnti. Equivale al pulsante **Fine** della **Pubblicazioneguidata**.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [How to: Specify Where Visual Studio Copies the Files](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [How to: Specify the Location Where End Users Will Install From](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [How to: Specify a Link for Technical Support](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [How to: Specify the ClickOnce Offline or Online Install Mode](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [How to: Enable AutoStart for CD Installations](../Topic/How%20to:%20Enable%20AutoStart%20for%20CD%20Installations.md)   
 [How to: Set the ClickOnce Publish Version](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [How to: Automatically Increment the ClickOnce Publish Version](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [How to: Specify Which Files Are Published by ClickOnce](../Topic/How%20to:%20Specify%20Which%20Files%20Are%20Published%20by%20ClickOnce.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [How to: Manage Updates for a ClickOnce Application](../Topic/How%20to:%20Manage%20Updates%20for%20a%20ClickOnce%20Application.md)   
 [How to: Change the Publish Language for a ClickOnce Application](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [How to: Specify a Start Menu Name for a ClickOnce Application](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [How to: Specify a Publish Page for a ClickOnce Application](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [ClickOnce Security and Deployment](../../deployment/clickonce-security-and-deployment.md)