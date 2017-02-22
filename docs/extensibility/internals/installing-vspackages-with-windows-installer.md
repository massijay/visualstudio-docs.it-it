---
title: "L&#39;installazione di VS con Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazione [Visual Studio SDK], con Windows Installer"
  - "Package VS, distribuzione"
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# L&#39;installazione di VS con Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'integrazione del package VS in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede più solo una copia di file nel computer di un utente.  Il programma di installazione del pacchetto VS necessario installare il pacchetto VS e i file dipendenti e registro e integrarli in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Il package VS possibile sfruttare le funzionalità di integrazione come visualizzare l'icona nella schermata iniziale di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e sulla finestra di dialogo.  
  
 I file di Microsoft Windows Installer sono la modalità consigliata per distribuire il package VS.  I package di Windows Installer di facile utilizzo possono essere eseguiti in qualsiasi sistema operativo Windows supportati da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere [Windows Installer](http://msdn.microsoft.com/it-it/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## In questa sezione  
 [Nozioni di base di Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Viene fornita una panoramica su Windows Installer.  
  
 [Scenari di installazione di VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Vengono illustrati i diversi modi in cui è possibile supportare le installazioni contemporanee di package VS che di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Creazione di un pacchetto di Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Vengono forniti cenni preliminari sui passaggi che tipici i programmi di installazione seguono correttamente per installare e integrare Vspackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Viene descritto come un programma di installazione può rilevare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e i relativi componenti e impostazione di annullamento se le richieste di package VS non vengono soddisfatti.  
  
 [Gestione dei componenti](../../extensibility/internals/component-management.md)  
 Viene descritto come sviluppare un programma di installazione che gestirà l'integrità delle versioni del prodotto precedenti.  
  
 [Scegliere la Directory di installazione per un VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Riepilogate le opzioni per l'individuazione del package VS.  
  
 [Registrazione di VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Viene illustrato come vengono registrati durante l'installazione e perché la registrazione automatica è corretta sincrono.  
  
 [Tipi di progetto di distribuzione](../../extensibility/internals/deploying-project-types.md)  
 Viene illustrato come utilizzare il nuovo aggregatore del tipo di progetto per i tipi di progetto di codice gestito.  
  
 [Procedura: generare le informazioni del Registro di sistema per un programma di installazione](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Viene illustrato come utilizzare RegPkg.exe per generare un manifesto di registrazione per un VSPackage gestito.  
  
 [Comandi devono essere eseguiti dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Viene illustrato come eseguire i comandi di postinstallazione1 integrare Vspackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Disinstallazione di un package VS con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Vengono descritti i passaggi che il programma di installazione deve eseguire quando gli utenti disinstallazione il package VS.  
  
## Sezioni correlate  
 [Installazione di VSPackage](../../misc/installing-vspackages.md)  
 Viene illustrato come compilare e installare Vspackage e come supportare gli utenti che eseguono più versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contemporaneamente.