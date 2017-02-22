---
title: "Distribuzione di estensioni di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Distribuzione VSIX"
  - "distribuzione VSIX"
  - "DLL satellite, nei pacchetti VSIX"
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Distribuzione di estensioni di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo aver completato lo sviluppo dell'estensione, installarlo in altri computer, condividere con amici e colleghi o pubblicarlo in Visual Studio Gallery. In questa sezione viene illustrato tutto è necessario eseguire per pubblicare e gestire l'estensione: utilizzo di file con estensione VSIX, pubblicazione, localizzazione e l'aggiornamento.  
  
## Utilizzo di estensioni VSIX  
 È possibile creare un estensioni VSIX creando un progetto VSIX vuoto e quindi aggiungere i modelli di elemento diverso. Per altre informazioni, vedere [Modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
 È possibile utilizzare il formato VSIX per modelli di progetto del pacchetto, elemento componenti di modelli, i package VS, Managed Extensibility Framework \(MEF\), **della casella degli strumenti** controlli, assembly e tipi personalizzati \(include pagine iniziali personalizzate\). Il formato VSIX utilizza la distribuzione basata su file. Per ulteriori informazioni sui pacchetti VSIX, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Il formato VSIX non supporta l'installazione di frammenti di codice. Non supporta inoltre alcuni altri scenari, ad esempio la scrittura alla Global Assembly Cache \(GAC\) o il Registro di sistema. Se è necessario scrivere nella Global Assembly Cache o nel Registro di sistema dell'installazione, è necessario utilizzare il programma di installazione di Windows. Per altre informazioni, vedere [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## Pubblicazione dell'estensione di Visual Studio Gallery  
 È possibile distribuire l'estensione ad altre persone sufficiente mailing tali file. VSIX o inserire in un server. Ma il modo migliore per ottenere il codice nelle mani di molte persone è inserita la [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847). Le estensioni di Visual Studio Gallery sono disponibili agli utenti di Visual Studio tramite **estensioni e aggiornamenti**. Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Per un esempio completo che illustra come caricare un'estensione di Visual Studio Gallery, vedere [Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## Raccolte private  
 Durante lo sviluppo di controlli, modelli e strumenti, è possibile condividerle con l'organizzazione inviando messaggi a una raccolta sulla rete intranet privata. Per altre informazioni, vedere [Raccolte private](../extensibility/private-galleries.md).  
  
## Localizzazione dell'estensione  
 Se si prevede di rilasciare l'estensione in impostazioni locali diverse, è necessario considerare la localizzazione. Per una spiegazione di che cosa comporta, vedere [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md).  
  
## L'aggiornamento e l'estensione di controllo delle versioni  
 Dopo aver pubblicato l'estensione, si giungerà volta quando è necessario aggiornarlo. Per scoprire come aggiornare un'estensione che è stata pubblicata nella raccolta di Visual Studio, vedere [Procedura: aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 È possibile impostare l'estensione per il supporto di più versioni di Visual Studio. Per altre informazioni, vedere [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|In questo articolo viene spiegato come utilizzare il modello di progetto VSIX per installare un modello di progetto personalizzato.|  
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Vengono descritti i componenti di un pacchetto VSIX.|  
|[Modello di progetto VSIX](../extensibility/vsix-project-template.md)|Vengono fornite istruzioni dettagliate su come creare un pacchetto e pubblicare un'estensione.|  
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire testo localizzato per il processo di installazione utilizzando file vsixlangpack.|  
|[Procedura: aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md)|Viene descritto come aggiornare un'estensione del sistema e su come distribuire un aggiornamento di un'estensione di Visual Studio esistente.|  
|[Procedura: aggiungere una dipendenza a un pacchetto VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Viene descritto come aggiungere riferimenti ai pacchetti di distribuzione VSIX.|  
|[Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Viene illustrato come distribuire un'estensione con Windows Installer.|  
|[Firma dei pacchetti VSIX](../extensibility/signing-vsix-packages.md)|Viene illustrato come firmare pacchetti VSIX.|  
|[Raccolte private](../extensibility/private-galleries.md)|Viene illustrato come creare raccolte private per le estensioni.|  
|[Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Viene illustrato come utilizzare il supporto delle estensioni di più versioni di Visual Studio.|