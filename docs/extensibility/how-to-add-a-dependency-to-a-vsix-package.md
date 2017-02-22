---
title: "Procedura: aggiungere una dipendenza a un pacchetto VSIX | Microsoft Docs"
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
  - "riferimento al pacchetto"
  - "assembly di pacchetto"
  - "dll del pacchetto"
  - "riferimento VSIX"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: aggiungere una dipendenza a un pacchetto VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile configurare una distribuzione del pacchetto VSIX che consente di installare tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze progetto VSIX del file source.extension.vsixmanifest.  
  
#### Per aggiungere una dipendenza  
  
1.  Aprire il file source.extension.vsixmanifest nel **Progettazione** visualizzazione. Andare alla **dipendenze** scheda e fare clic su **New**.  
  
2.  Per aggiungere un'estensione installata: nel **Aggiungi nuova dipendenza** nella finestra di dialogo **estensione installata** e quindi, per il **nome**, selezionare un'estensione nell'elenco.  
  
3.  Per aggiungere un altro progetto VSIX che non è installato:: nel **Aggiungi nuova dipendenza** nella finestra di dialogo **File nel file system** e quindi utilizzare il **Sfoglia** pulsante per selezionare il pacchetto VSIX.  
  
## Vedere anche  
 [Riferimento dello Schema 1.0 estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)