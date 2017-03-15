---
title: "How to: Re-sign Application and Deployment Manifests | Microsoft Docs"
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
  - "Office applications, signing manifests"
  - "deploying applications [ClickOnce], signing manifests"
  - "deploying applications, signing manifests"
  - "ClickOnce deployment, signing manifests"
  - "Office development in Visual Studio, signing manifests"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# How to: Re-sign Application and Deployment Manifests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo avere apportato modifiche alle proprietà di distribuzione nel manifesto dell'applicazione per le applicazioni Windows Form, le applicazioni Windows Presentation Foundation \(xbap\) o le soluzioni Office, è necessario ripetere la firma dei manifesti dell'applicazione e della distribuzione con un certificato.  Questo processo assicura che nei computer degli utenti finali non vengano installati file alterati.  
  
 Un altro scenario in cui è possibile ripetere la firma dei manifesti si verifica quando i clienti desiderano firmare i manifesti dell'applicazione e della distribuzione con il proprio certificato.  
  
## Nuova firma dei manifesti dell'applicazione e di distribuzione  
 In questa procedura si presuppone che il file manifesto dell'applicazione \(manifest\) sia già stato modificato.  Per ulteriori informazioni, vedere [Procedura: modificare le proprietà di distribuzione](http://msdn.microsoft.com/it-it/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### Per firmare nuovamente i manifesti dell'applicazione e di distribuzione con Mage.exe  
  
1.  Aprire una finestra **Prompt dei comandi di Visual Studio**.  
  
2.  Impostare le directory sulla cartella in cui sono contenuti i file del manifesto che si desidera firmare.  
  
3.  Digitare il comando seguente per firmare il file del manifesto dell'applicazione.  Sostituire ManifestFileName con il nome del file manifesto e l'estensione.  Sostituire Certificate con il percorso relativo o completo del file di certificato e sostituire Password con la password del certificato.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     È possibile, ad esempio, eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.  I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Digitare il comando seguente per aggiornare e firmare il file manifesto della distribuzione, sostituendo i nomi dei segnaposto come nel passaggio precedente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     È ad esempio possibile eseguire il comando seguente per aggiornare e firmare un manifesto della distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Facoltativamente, copiare il manifesto della distribuzione master \(publish\\*appname*.application\) nella directory di distribuzione della versione \(publish\\Application Files\\*appname*\_*version*\).  
  
## Aggiornamento e nuova firma dei manifesti dell'applicazione e di distribuzione  
 In questa procedura si presuppone che il file manifesto dell'applicazione \(con estensione manifest\) sia già stato modificato, ma che esistano anche altri file aggiornati.  Quando i file vengono aggiornati, è necessario aggiornare anche gli hash che li rappresentano.  
  
#### Per aggiornare e firmare nuovamente i manifesti dell'applicazione e di distribuzione con Mage.exe  
  
1.  Aprire una finestra **Prompt dei comandi di Visual Studio**.  
  
2.  Impostare le directory sulla cartella in cui sono contenuti i file del manifesto che si desidera firmare.  
  
3.  Rimuovere l'estensione di file deploy dai file nella cartella di output di pubblicazione.  
  
4.  Digitare il comando seguente per aggiornare il manifesto dell'applicazione con i nuovi hash per i file aggiornati e firmare il file manifesto dell'applicazione.  Sostituire ManifestFileName con il nome del file manifesto e l'estensione.  Sostituire Certificate con il percorso relativo o completo del file di certificato e sostituire Password con la password del certificato.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     È possibile, ad esempio, eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.  I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Digitare il comando seguente per aggiornare e firmare il file manifesto della distribuzione, sostituendo i nomi dei segnaposto come nel passaggio precedente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     È ad esempio possibile eseguire il comando seguente per aggiornare e firmare un manifesto della distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Form o un'applicazione browser Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Aggiungere nuovamente l'estensione file deploy ai file, ad eccezione dei file manifesto della distribuzione e dell'applicazione.  
  
7.  Facoltativamente, copiare il manifesto della distribuzione master \(publish\\*appname*.application\) nella directory di distribuzione della versione \(publish\\Application Files\\*appname*\_*version*\).  
  
## Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)