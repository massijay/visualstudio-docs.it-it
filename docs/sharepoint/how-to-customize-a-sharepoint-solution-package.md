---
title: "Procedura: personalizzare un pacchetto della soluzione SharePoint"
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
  - "VS.SharePointTools.RAD.PackageDesignerAdvanced"
  - "VS.SharePointTools.RAD.PackageDesigner.Manifest"
  - "VS.SharePointTools.RAD.PackageDesignerProperties"
  - "VS.SharePointTools.RAD.PackageDesigner.SwitchView"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, pacchetti"
ms.assetid: fd365f8c-8a80-4ce8-8e28-c0eb609f12f3
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: personalizzare un pacchetto della soluzione SharePoint
  Per creare e personalizzare un pacchetto \(con estensione wsp\) è possibile utilizzare la finestra di progettazione del pacchetto.  Ad esempio si possono aggiungere gli elementi e le funzionalità del progetto SharePoint, specificare se il server Web viene reimpostato quando la soluzione viene distribuita e impostare il tipo di server di distribuzione.  
  
## Apertura della finestra di progettazione del pacchetto  
  
#### Per aprire la finestra di progettazione del pacchetto  
  
-   In **Esplora soluzioni**, fare doppio clic su **Pacchetto**, oppure scegliere **Progettazione viste** dal menu di scelta rapida per **Pacchetto**.  
  
## Visualizzazione del file manifesto nel pacchetto  
 Per modificare e generare il file manifesto nel pacchetto è possibile utilizzare la finestra di progettazione del pacchetto.  Successivamente è possibile visualizzare il codice XML per questo file in Visual Studio.  
  
#### Per visualizzare il file di origine XML  
  
1.  In **Progettazione pacchetti**, scegliere **Manifesto**.  
  
#### Per visualizzare il file manifesto nel pacchetto tramite Esplora soluzioni  
  
1.  In **Esplora soluzioni** selezionare **Mostra tutti i file**.  
  
2.  Espandere pacchetto, espandere Package.package e aprire il file Package.Template.xml.  
  
    > [!NOTE]  
    >  Quando si apre il file manifesto in formato XML per il modello del pacchetto, i file vengono automaticamente convalidati ed è possibile ignorare gli avvisi che vengono visualizzati nella finestra Elenco errori.  
  
## Modifica del modello di manifesto  
 Il codice XML per il file manifesto nel pacchetto può essere modificato nell'editor XML di Visual Studio o nel riquadro Modello di manifesto.  Per qualsiasi modifica al codice XML viene eseguito il merge all'interno del file manifesto per il pacchetto.  
  
#### Per modificare il modello di manifesto tramite l'editor XML  
  
1.  In **Progettazione pacchetti**, scegliere la scheda **Manifesto**, espandere il nodo **Opzioni di modifica** quindi scegliere il collegamento **Apri in XML Editor**.  
  
     Le modifiche apportate al codice XML vengono incluse al file manifesto nel pacchetto.  
  
#### Per modificare il modello di manifesto tramite il riquadro Modello di manifesto  
  
1.  In **Progettazione pacchetti**, scegliere la scheda **Manifesto**, espandere il nodo **Opzioni di modifica** quindi modificare l'XML visualizzato nel riquadro Modello di manifesto.  
  
     Le modifiche apportate al codice XML vengono visualizzate nel riquadro **Anteprima del manifesto nel pacchetto**.  
  
## Sovrascrittura del file manifesto nel pacchetto  
 È possibile disabilitare la finestra di progettazione del pacchetto e creare manualmente il file manifest.xml.  Alla prima esecuzione di questa procedura, le impostazioni correnti della finestra di progettazione del pacchetto vengono salvate nel file XML del modello del pacchetto.  Successivamente, è possibile modificare o sovrascrivere il codice XML.  
  
> [!NOTE]  
>  Se si aggiungono o rimuovono elementi e funzionalità del progetto SharePoint dal file XML mentre la finestra di progettazione del pacchetto è disabilitata, questi elementi e funzionalità del progetto non vengono inclusi nel pacchetto.  
  
#### Per sovrascrivere il file manifesto incluso nel pacchetto disabilitando la finestra di progettazione  
  
1.  In **Progettazione pacchetti**, selezionare la scheda **Manifesto**.  
  
2.  .  
  
3.  Espandere il nodo **Opzioni di modifica**, scegliere il collegamento **Sovrascrivi l'XML generato e modifica manifesto nell'editor XML** quindi scegliere il pulsante **Sì**.  
  
     Il modello viene aggiornato con il file manifesto attualmente incluso nel pacchetto.  
  
## Abilitazione della finestra di progettazione del pacchetto  
 È possibile riabilitare la finestra di progettazione del pacchetto per personalizzare il file manifest.xml.  
  
#### Per riabilitare la finestra di progettazione  
  
1.  In **Progettazione pacchetti**, scegliere il collegamento **Rimuovere le modifiche del manifesto e riabilitare la finestra di progettazione** quindi scegliere il pulsante **Sì**.  
  
     Il modello viene aggiornato con il testo originale e vengono perse tutte le modifiche apportate al codice XML.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  