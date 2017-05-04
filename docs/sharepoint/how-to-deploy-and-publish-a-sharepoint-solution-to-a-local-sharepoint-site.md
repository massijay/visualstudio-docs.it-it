---
title: "Procedura: distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "distribuzione [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, distribuzione"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale
  Le soluzioni SharePoint possono essere distribuite o pubblicate nel server SharePoint locale del computer di sviluppo.  Il processo di distribuzione consente di copiare il file con estensione wsp nel server SharePoint, di installare la soluzione, nonché di attivare le funzionalità.  Il processo di pubblicazione copia solo il file con estensione wsp nel server SharePoint e lo installa.  È necessario attivarlo manualmente per abilitarlo in SharePoint.  
  
## Per distribuire una soluzione SharePoint nel server SharePoint locale  
  
1.  In **Esplora soluzioni** scegliere il progetto che si desidera distribuire.  
  
2.  Sulla barra dei menu scegliere **Compilazione**, **Distribuisci soluzione**.  
  
     Il file con estensione wsp viene creato e installato nel server SharePoint locale.  Inoltre vengono attivate le funzionalità.  
  
## Per pubblicare una soluzione SharePoint in un server SharePoint locale  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto di SharePoint che si vuole pubblicare, quindi scegliere **Pubblica**.  
  
2.  Nella finestra di dialogo **Pubblica**, scegliere il pulsante di opzione **Pubblica su file system**.  
  
3.  Nella casella di testo **Percorso di destinazione**, immettere un percorso locale e quindi scegliere il pulsante **Pubblica**.  
  
     Lo stato di avanzamento della pubblicazione viene visualizzato nella finestra di Visual Studio **Output**.  Al termine del processo, il file di soluzione \(.wsp\) viene installato nel server SharePoint locale.  Tuttavia, deve comunque essere attivato per essere utilizzato in SharePoint.  Se il file di soluzione esiste già, si verifica un errore e viene chiesto se si desidera sovrascrivere il file esistente.  Per informazioni sull'aggiornamento di un pacchetto, vedere la sezione sui pacchetti remoti di aggiornamento in [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Vedere anche  
 [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Creazione di pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  