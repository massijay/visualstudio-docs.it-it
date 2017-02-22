---
title: "Creazione di un pacchetto di Windows Installer | Microsoft Docs"
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
  - "file con estensione msi, i package VS"
  - "file MSI, i package VS"
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un pacchetto di Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Unità dati del modello di Windows Installer. Anziché scrivere uno script contenente le procedure per copiare i file e la scrittura di voci del Registro di sistema, ad esempio, è possibile creare righe e colonne nelle tabelle di database che contengono dati di file e Registro di sistema.  
  
## Voci di database  
 Per installare un pacchetto Visual Studio, un pacchetto Windows Installer deve contenere le voci di database per eseguire le attività seguenti:  
  
-   Il sistema per individuare le versioni di ricerca [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il pacchetto Visual Studio supporta \(utilizzando le tabelle di Windows Installer che includono AppSearch, CompLocator, RegLocator, DrLocator e firma\).  
  
-   Annullare l'installazione se nessuna versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è installato o se non viene soddisfatto un altro requisito di sistema del VSPackage \(utilizzando la tabella LaunchCondition\).  
  
-   Installare il pacchetto Visual Studio e file dipendenti \(utilizzando la directory, componente e tabelle di file\).  
  
-   Aggiungere le informazioni appropriate per il package VS nel Registro di sistema \(utilizzando la tabella del Registro di sistema\).  
  
-   Integrare il pacchetto Visual Studio in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamando **devenv.exe \/setup** \(utilizzando la tabella CustomAction\).  
  
 Per ulteriori informazioni, vedere [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## Strumenti di installazione  
 Un'ampia gamma di strumenti di installazione di terze parti offrono un ambiente di sviluppo per i pacchetti di Windows Installer. Due strumenti gratuiti sono i seguenti:  
  
-   InstallShield Limited Edition  
  
     È possibile ottenere una versione limitata di InstallShield tramite Visual Studio **Nuovo progetto** finestra di dialogo. Espandere **altri tipi di progetto** e quindi selezionare **installazione e distribuzione**. Selezionare il modello di InstallShield.  
  
-   set di strumenti XML di Windows Installer  
  
     Il set di strumenti Compila i pacchetti di Windows Installer dal file di origine XML. Il set di strumenti è un progetto open source di Microsoft. È possibile scaricare il codice sorgente e i file eseguibili da [http:\/\/sourceforge.net\/projects\/wix](http://sourceforge.net/projects/wix).  
  
 Per i prodotti commerciali integrano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vedere [http:\/\/visualstudiogallery.com](http://visualstudiogallery.com/).  
  
## Vedere anche  
 [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)