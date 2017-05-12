---
title: "Procedura: aggiungere e rimuovere funzionalit&#224; ed elementi in un pacchetto utilizzando Esplora pacchetti | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, pacchetti"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: aggiungere e rimuovere funzionalit&#224; ed elementi in un pacchetto utilizzando Esplora pacchetti
  Per configurare un pacchetto al fine di distribuire gli elementi e le funzionalità SharePoint, è possibile utilizzare Esplora pacchetti.  Gli elementi di progetto e le funzionalità SharePoint possono essere regolati nel file con estensione wsp.  
  
 In alternativa, è possibile utilizzare la finestra di progettazione del pacchetto per visualizzare e riordinare le funzionalità al fine di modificare l'ordine di attivazione.  Per ulteriori informazioni, vedere [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## Apertura di Esplora pacchetti  
 Per aprire Esplora pacchetti è possibile utilizzare la procedura riportata di seguito, se la soluzione di Visual Studio dispone almeno di un progetto SharePoint.  In alternativa, Esplora pacchetti viene aperto automaticamente quando si visualizza una finestra di progettazione della funzionalità o del pacchetto.  Dopo aver chiuso tutte le finestre di progettazione della funzionalità e del pacchetto, viene chiuso anche Esplora pacchetti.  
  
#### Per aprire Esplora pacchetti  
  
1.  Nella barra dei menu scegliere **Visualizza**, **Altre finestre**, **Esplora pacchetti**.  
  
     **Esplorapacchetti** viene visualizzato nella Casella degli strumenti.  
  
## Aggiunta di una funzionalità a un pacchetto  
 Tramite Esplora pacchetti è possibile aggiungere funzionalità nuove ed esistenti a un pacchetto.  
  
#### Per aggiungere una funzionalità SharePoint  
  
1.  Aprire **Esplora pacchetti**, aprire il menu di scelta rapida del progetto e quindi scegliere **Aggiungi funzionalità**.  
  
#### Per spostare una funzionalità SharePoint esistente  
  
1.  Aprire **Esplora pacchetti**, quindi eseguire una delle operazioni seguenti:  
  
    -   Trascinare una **Funzionalità** da un progetto a un altro.  
  
    -   Aprire il menu di scelta rapida per una funzionalità, scegliere **Taglia**, aprire il menu di scelta rapida del progetto in cui si desidera spostare la funzionalità quindi scegliere **Incolla**.  
  
    > [!NOTE]  
    >  Utilizzare questa procedura se nella soluzione sono presenti diversi progetti SharePoint.  
  
## Convalida di una funzionalità o un pacchetto  
 Convalidando i file è possibile individuare potenziali problemi nei pacchetti e nelle funzionalità SharePoint.  Gli avvisi e gli errori vengono visualizzati nelle finestre Output ed Elenco errori.  
  
#### Per convalidare un pacchetto o una funzionalità SharePoint  
  
1.  Aprire **Esplora pacchetti**.  
  
2.  Aprire un menu di scelta rapida per una funzionalità o un pacchetto e quindi scegliere **Convalida**.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  