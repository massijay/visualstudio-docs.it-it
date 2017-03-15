---
title: "Tabella di comandi di Visual Studio (. File Vsct) | Microsoft Docs"
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
  - "File VSCT, panoramica"
  - "Visual Studio comando tabella file di configurazione (VSCT), panoramica"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Tabella di comandi di Visual Studio (. File Vsct)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un file di configurazione nella tabella di comando è un file di testo che descrive il set di comandi che contiene un VSPackage. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando tabella \(VSCT\) viene compilato il file di configurazione basato su XML \(file. vsct\) in file di output \(.cto\) tabella comando binario. I file risultanti .cto sono gli stessi di quelli creati tramite il compilatore di tabella \(CTC\) del comando per compilare i file di configurazione .ctc. Tuttavia, file. vsct basato su XML presenta alcuni vantaggi, ad esempio un editor XML e XML IntelliSense.  
  
 Per ulteriori informazioni sulla sintassi e semantica del file. vsct, vedere [Progettazione tabella comandi XML \(. File Vsct\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## In questa sezione  
 [Progettazione tabella comandi XML \(. File Vsct\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Viene descritto come progettare i file. vsct.  
  
 [Procedura: creare una. File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Confronta i metodi per la creazione di un file vsct. Viene descritto il processo per la creazione manuale di un nuovo file. vsct.  
  
## Sezioni correlate  
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornisce informazioni dettagliate su ogni sezione del file di configurazione XML nella tabella di comando.  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/it-it/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Viene presentata una panoramica del formato di file .ctc obsoleto.  
  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descrive la specifica di formato di tabella comandi.  
  
 [Risorse in VS](../../extensibility/internals/resources-in-vspackages.md)  
 Viene descritto come utilizzare le risorse gestite e VSPackages gestito.  
  
 [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Viene illustrato come creare un'interfaccia utente che include i menu, barre degli strumenti e caselle combinate di comando.