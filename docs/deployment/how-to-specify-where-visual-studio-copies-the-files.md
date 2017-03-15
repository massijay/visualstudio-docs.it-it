---
title: "How to: Specify Where Visual Studio Copies the Files | Microsoft Docs"
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
  - "publishing, specifying location"
  - "Publish Location property"
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Specify Where Visual Studio Copies the Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si pubblica un'applicazione tramite ClickOnce, la proprietà `Publish Location` specifica il percorso in cui vengono inseriti i file dell'applicazione e il manifesto.  Può trattarsi di un percorso di file o del percorso di un server FTP.  
  
 È possibile specificare la proprietà `Publish Location` nella pagina **Pubblica** di **Progettazione progetti** oppure mediante la Pubblicazione guidata.  Per altre informazioni vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
> [!NOTE]
>  Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato.  L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.  
  
### Per specificare un percorso di pubblicazione  
  
1.  Con il progetto selezionato in **Esplora soluzioni** scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nel campo **Percorso pubblicazione** immettere il percorso di pubblicazione usando uno dei formati seguenti:  
  
    -   Per pubblicare in una condivisione file o in un percorso su disco, immettere il percorso usando un percorso UNC \(\\\\Server\\NomeApplicazione\) o un percorso file \(C:\\Deploy\\NomeApplicazione\).  
  
    -   Per pubblicare in un server FTP, immettere il percorso nel formato ftp:\/\/ftp.microsoft.com\/NomeApplicazione.  
  
     Si noti che il testo deve essere presente nella scheda **Posizione di pubblicazione** perché il pulsante Sfoglia \(**...**\) funzioni.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)