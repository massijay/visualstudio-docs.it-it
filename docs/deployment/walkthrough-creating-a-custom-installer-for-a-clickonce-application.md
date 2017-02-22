---
title: "Walkthrough: Creating a Custom Installer for a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "ClickOnce deployment, custom installer"
  - "installer [ClickOnce], custom"
  - "deploying applications [ClickOnce], custom installer"
  - "InPlaceHostingManager [ClickOnce], custom installer"
  - "custom installer [ClickOnce]"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Creating a Custom Installer for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Qualsiasi applicazione ClickOnce basata su un con estensione file exe può essere installata in modo invisibile all'utente e può essere aggiornata da un programma di installazione personalizzato.  Un programma di installazione personalizzato può fornire un'esperienza utente migliorata durante l'installazione, includendo finestre di dialogo personalizzate per operazioni di sicurezza e manutenzione.  Per eseguire operazioni di installazione, il programma di installazione personalizzato utilizza la classe <xref:System.Deployment.Application.InPlaceHostingManager>.  Questa procedura dettagliata dimostra come creare un programma di installazione personalizzato che installa in modo invisibile all'utente un'applicazione ClickOnce.  
  
## Prerequisiti  
  
### Per creare un programma di installazione personalizzato di un'applicazione ClickOnce  
  
1.  Nell'applicazione ClickOnce aggiungere riferimenti a System.Deployment e System.Windows.Forms.  
  
2.  Aggiungere una nuova classe all'applicazione e specificare un nome.  In questa procedura dettagliata viene utilizzato il nome `MyInstaller`.  
  
3.  Aggiungere le istruzioni `Imports` o `using` seguenti all'inizio della nuova classe.  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Aggiungere i metodi seguenti alla classe.  
  
     Questi metodi chiamano i metodi <xref:System.Deployment.Application.InPlaceHostingManager> per scaricare il manifesto della distribuzione, asserire le autorizzazioni appropriate, chiedere all'utente l'autorizzazione per l'installazione, quindi scaricare e installare l'applicazione nella cache di ClickOnce.  In un programma di installazione personalizzato è possibile specificare che un'applicazione ClickOnce è stata precedentemente considerata attendibile oppure rinviare la decisione sull'attendibilità al momento della chiamata al metodo <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>.  Questo codice rende precedentemente attendibile l'applicazione.  
  
    > [!NOTE]
    >  Le autorizzazioni assegnate mediante assegnazione precedente dell'attendibilità non possono superare le autorizzazioni del codice del programma di installazione personalizzato.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Per tentare l'installazione dal codice, chiamare il metodo `InstallApplication`.  Ad esempio, se la classe è stata denominata `MyInstaller`, è possibile chiamare `InstallApplication` nel modo descritto di seguito.  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## Passaggi successivi  
 Un'applicazione ClickOnce può anche aggiungere una logica di aggiornamento personalizzata, inclusa un'interfaccia utente personalizzata da visualizzare durante il processo di aggiornamento.  Per ulteriori informazioni, vedere <xref:System.Deployment.Application.UpdateCheckInfo>.  Un'applicazione ClickOnce può inoltre eliminare la voce del menu Start standard, il collegamento e la voce Installazione applicazioni mediante l'elemento `<customUX>`.  Per ulteriori informazioni, vedere [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## Vedere anche  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md)