---
title: 'Procedura: distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4959334c9d6949e199ad18934e69ea46e1172b55
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Procedura: distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale
  È possibile distribuire o pubblicare le soluzioni SharePoint in un server SharePoint locale nel computer di sviluppo. Il processo di distribuzione copia il file con estensione wsp nel server SharePoint, installa la soluzione e quindi attiva le funzionalità. Il processo di pubblicazione solo copia il file con estensione wsp nel server SharePoint e lo installa. È necessario attivare manualmente per abilitarlo in SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Per distribuire una soluzione di SharePoint nel server SharePoint locale  
  
1.  In **Esplora**, scegliere il progetto che si desidera distribuire.  
  
2.  Nella barra dei menu, scegliere **compilare**, **Distribuisci soluzione**.  
  
     Il file con estensione wsp viene creato e installato nel server SharePoint locale. Inoltre, vengono attivate le funzionalità.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Per pubblicare una soluzione di SharePoint in un server SharePoint locale  
  
1.  In **Esplora**, aprire il menu di scelta rapida per il progetto di SharePoint che si desidera pubblicare e quindi scegliere **pubblica**.  
  
2.  Nel **pubblica** finestra di dialogo scegliere la **pubblica su File System** pulsante di opzione.  
  
3.  Nel **percorso di destinazione** casella di testo, immettere un percorso locale e quindi scegliere il **pubblica** pulsante.  
  
     Viene visualizzato lo stato di pubblicazione in Visual Studio **Output** finestra. Al termine del processo, il file di soluzione (con estensione wsp) è installato nel server SharePoint locale. Tuttavia, deve ancora essere attivato per essere utilizzati in SharePoint. Se il file di soluzione esiste già, l'errore si verifica e viene chiesto se si desidera sovrascrivere il file esistente. Per informazioni sull'aggiornamento del pacchetto, vedere la sezione sull'aggiornamento di pacchetti remoti in [procedura: distribuire, pubblicare e aggiornare le soluzioni SharePoint in un Server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un Server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Creazione di pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Procedura: personalizzare un pacchetto di soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  