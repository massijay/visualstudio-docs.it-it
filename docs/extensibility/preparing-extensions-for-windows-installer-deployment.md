---
title: "Preparazione di estensioni per la distribuzione di Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msi VSIX"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Preparazione di estensioni per la distribuzione di Windows Installer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare un pacchetto di Windows Installer \(MSI\) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione di MSI. In questo documento viene illustrato come preparare un progetto di output il cui valore predefinito è un pacchetto VSIX per l'inclusione in un progetto di installazione.  
  
## Preparazione di un progetto di estensione per la distribuzione di Windows Installer  
 Eseguire questi passaggi nei nuovi progetti di estensione prima di aggiungere a un progetto di installazione.  
  
#### Per preparare un progetto di estensione per la distribuzione di Windows Installer  
  
1.  Creare un VSPackage, componente MEF, Adornment Editor o altro tipo di progetto di estensibilità che include un manifesto VSIX.  
  
2.  Aprire il manifesto VSIX nell'editor di codice.  
  
3.  Impostare l'elemento InstalledByMsi del manifesto VSIX per `true`. Per ulteriori informazioni sul manifesto VSIX, vedere [Riferimento dello Schema 2.0 estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Ciò impedisce che il programma di installazione VSIX il tentativo di installare il componente.  
  
4.  Pulsante destro del mouse sul progetto in **Esplora** e fare clic su **proprietà**.  
  
5.  Selezionare il **VSIX** scheda.  
  
6.  Selezionare la casella **contenuto VSIX copia nel percorso seguente** e digitare il percorso in cui il progetto di installazione verrà prelevati i file.  
  
## Estrazione dei file da un pacchetto VSIX esistente  
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando si dispone di file di origine.  
  
#### Per estrarre i file da un pacchetto VSIX esistente  
  
1.  Rinominare il. File VSIX che contiene l'estensione da *filename*. VSIX per *filename*. zip.  
  
2.  Copiare il contenuto del file zip in una directory.  
  
3.  Eliminare il file XML \[Content\_types\] dalla directory.  
  
4.  Modificare il manifesto VSIX, come illustrato nella procedura precedente.  
  
5.  Aggiungere i file rimanenti al progetto di installazione.  
  
## Vedere anche  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/it-it/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/it-it/4bd4b63a-2b91-431e-839c-5752443f0eaf)