---
title: "Procedura: personalizzare una funzionalit&#224; SharePoint | Microsoft Docs"
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
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, funzionalità"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Procedura: personalizzare una funzionalit&#224; SharePoint
  È possibile creare e personalizzare funzionalità SharePoint tramite la finestra di progettazione della funzionalità di Visual Studio.  Ad esempio è possibile impostare l'ambito della funzionalità e aggiungere altre funzionalità come dipendenze.  Per impostazione predefinita, la finestra di progettazione della funzionalità viene aperta quando si aggiunge una nuova funzionalità in Esplora soluzioni o Esplora pacchetti di SharePoint.  
  
## Apertura della finestra di progettazione della funzionalità  
 Tramite la finestra di progettazione della funzionalità è possibile aggiungere o rimuovere elementi del progetto SharePoint da una funzionalità.  
  
#### Per aprire la finestra di progettazione della funzionalità  
  
1.  In **Esplora soluzioni** espandere **Funzionalità**.  
  
2.  Fare doppio clic sull'elemento *Feature1* o aprire il menu di scelta rapida per l'elemento *Feature1* e quindi scegliere **Progettazione viste**.  
  
## Visualizzazione del file manifesto nel pacchetto  
 La finestra di progettazione della funzionalità può essere utilizzata per modificare e generare il file manifesto nel pacchetto per la funzionalità \(feature.xml\).  Successivamente è possibile visualizzare il codice XML per questo file in Visual Studio.  
  
#### Per visualizzare il file manifesto nel pacchetto  
  
1.  In **Progettazione funzionalità**, scegliere la scheda **Manifesto**.  
  
#### Per visualizzare il file manifesto nel pacchetto tramite Esplora soluzioni  
  
1.  In **Esplora soluzioni**, selezionare l'icona **Mostra tutti i file**.  
  
2.  Espandere funzionalità, espandere Nomefunzionalità, espandere Nomefunzionalità.feature e aprire il file *FeatureName*.Template.xml.  
  
    > [!NOTE]  
    >  Quando si apre il file XML manifesto del modello funzionalità, i file vengono convalidati automaticamente ed è possibile ignorare gli avvisi visualizzati nella finestra Elenco errori.  
  
## Modifica del modello di manifesto  
 Il codice XML per il file manifesto della funzionalità può essere modificato nell'editor XML di Visual Studio o nel riquadro Modello di manifesto.  Qualsiasi modifica al codice XML viene inclusa al file manifesto nel pacchetto per la funzionalità.  Ad esempio potrebbe essere necessario modificare il modello di manifesto per personalizzare una proprietà della funzionalità.  
  
#### Per modificare il modello di manifesto tramite l'editor XML  
  
1.  In **Progettazione funzionalità**, scegliere la scheda **Manifesto**, espandere il nodo di **Opzioni di modifica** quindi scegliere il collegamento **Apri in XML Editor**.  
  
     Le modifiche apportate al codice XML vengono incluse al file manifesto nel pacchetto.  
  
#### Per modificare il modello di manifesto tramite il riquadro Modello di manifesto  
  
1.  In **Progettazione funzionalità**, scegliere la scheda **Manifesto**, espandere il nodo **Opzioni di modifica** quindi modificare l'XML visualizzato nel riquadro Modello di manifesto.  
  
     Le modifiche apportate al codice XML vengono visualizzate nel riquadro **Anteprima del manifesto nel pacchetto**.  
  
## Sovrascrittura del file manifesto nel pacchetto  
 È possibile disabilitare la finestra di progettazione della funzionalità e creare manualmente il file feature.xml.  Alla prima esecuzione di questa procedura, le impostazioni correnti della finestra di progettazione della funzionalità vengono salvate nel file XML del modello funzionalità.  Successivamente, è possibile modificare o sovrascrivere il codice XML.  
  
> [!NOTE]  
>  Se si aggiungono o rimuovono elementi del progetto SharePoint dal file XML mentre la finestra di progettazione della funzionalità è disabilitata, questi elementi del progetto non vengono inclusi nel pacchetto.  
  
#### Per sovrascrivere il file manifesto incluso nel pacchetto disabilitando la finestra di progettazione  
  
1.  In **Progettazione funzionalità**, scegliere la scheda **Manifesto**.  
  
2.  Espandere il nodo **Opzioni di modifica**, scegliere il collegamento **Sovrascrivi l'XML generato e modifica manifesto nell'editor XML** quindi scegliere il pulsante **Sì**.  
  
     Il modello viene aggiornato con il file manifesto attualmente incluso nel pacchetto.  
  
## Abilitazione della finestra di progettazione della funzionalità  
 È possibile riabilitare la finestra di progettazione della funzionalità per personalizzare il file feature.xml.  
  
#### Per riabilitare la finestra di progettazione  
  
1.  In **Progettazione funzionalità**, scegliere il collegamento **Rimuovere le modifiche del manifesto quindi riabilitare la finestra di progettazione** quindi scegliere il pulsante **Sì**.  
  
2.  Il modello viene aggiornato con il testo originale e vengono perse tutte le modifiche apportate al codice XML.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  