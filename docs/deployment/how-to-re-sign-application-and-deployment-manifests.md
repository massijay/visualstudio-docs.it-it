---
title: 'Procedura: firmare manifesti di applicazione e distribuzione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: baa3e9310946482a4c7c64fdb619ce612a21dbda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Procedura: ripetere la firma dei manifesti dell'applicazione e di distribuzione
Dopo aver apportato modifiche alle proprietà di distribuzione nel manifesto dell'applicazione per applicazioni Windows Form, le applicazioni Windows Presentation Foundation (xbap) o soluzioni Office, è necessario firmare nuovamente l'applicazione e i manifesti di distribuzione con un certificato. Questo processo aiuta ad assicurare che nei computer degli utenti finali non sono installati file alterati.  
  
 Un altro scenario in cui è possibile firmare nuovamente i manifesti è quando si desiderano che i clienti firmare l'applicazione e i manifesti di distribuzione con il proprio certificato.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Firma nuovamente l'applicazione e distribuzione di manifesti  
 Questa procedura si presuppone che sono già state apportate modifiche al file manifesto dell'applicazione (con estensione manifest). Per ulteriori informazioni, vedere [procedura: modificare le proprietà di distribuzione](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per firmare nuovamente l'applicazione e distribuzione di manifesti con Mage.exe  
  
1.  Aprire un **prompt dei comandi di Visual Studio** finestra.  
  
2.  Passare alla cartella che contiene i file manifesto che si desidera accedere.  
  
3.  Digitare il comando seguente per firmare il file manifesto dell'applicazione. Sostituire ManifestFileName con il nome del file manifesto e l'estensione. Sostituire certificati con il percorso relativo o completo del file di certificato e la Password con la password per il certificato.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser di Windows Presentation Foundation. I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi dei segnaposto come nel passaggio precedente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Form o un'applicazione browser di Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Facoltativamente, copiare il manifesto della distribuzione master (pubblicare\\*appname*Application) nella directory di distribuzione della versione (publish\Application Files\\*appname*_ *versione*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>L'aggiornamento e firmare di nuovo l'applicazione e i manifesti di distribuzione  
 Questa procedura si presuppone che sono già state apportate modifiche all'applicazione (con estensione manifest) file manifesto, ma che non esistono altri file che sono stati aggiornati. Quando i file vengono aggiornati, il valore hash che rappresenta il file è necessario aggiornare.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Per aggiornare e firmare nuovamente l'applicazione e distribuzione di manifesti con Mage.exe  
  
1.  Aprire un **prompt dei comandi di Visual Studio** finestra.  
  
2.  Passare alla cartella che contiene i file manifesto che si desidera accedere.  
  
3.  Rimuovere l'estensione di file. deploy dai file nella cartella di output di pubblicazione.  
  
4.  Digitare il comando seguente per aggiornare il manifesto dell'applicazione con il nuovo hash per i file aggiornati e firmare il file manifesto dell'applicazione. Sostituire ManifestFileName con il nome del file manifesto e l'estensione. Sostituire certificati con il percorso relativo o completo del file di certificato e la Password con la password per il certificato.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per firmare un manifesto dell'applicazione per un componente aggiuntivo, un'applicazione Windows Form o un'applicazione browser di Windows Presentation Foundation. I certificati temporanei creati da Visual Studio non sono consigliati per la distribuzione in ambienti di produzione.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Digitare il comando seguente per aggiornare e firmare il file manifesto di distribuzione, sostituendo i nomi dei segnaposto come nel passaggio precedente.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Ad esempio, è possibile eseguire il comando seguente per aggiornare e firmare un manifesto di distribuzione per un componente aggiuntivo di Excel, un'applicazione Windows Form o un'applicazione browser di Windows Presentation Foundation.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Aggiungere l'estensione di file deploy al file, ad eccezione del fatto file manifesto dell'applicazione e distribuzione.  
  
7.  Facoltativamente, copiare il manifesto della distribuzione master (pubblicare\\*appname*Application) nella directory di distribuzione della versione (publish\Application Files\\*appname*_ *versione*).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per le applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [Procedura: abilitare le impostazioni di sicurezza ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: Debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un Computer Client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Procedura: Configurare il comportamento di richiesta di attendibilità di ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)