---
title: "Procedura: aggiungere e rimuovere cartelle mappate"
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
  - "VS.SharePointTools.Project.MappedFolder"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "cartelle mappate [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, cartelle mappate"
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Procedura: aggiungere e rimuovere cartelle mappate
  Alcune cartelle utilizzate comunemente nel server SharePoint, come Immagini e Layout, sono eccessivamente incorporate nella gerarchia dei file.  Queste cartelle possono essere mappate in un progetto SharePoint per accedervi più facilmente.  Le cartelle mappate sono le cartelle del progetto SharePoint che corrispondono alla posizione fisica dei file nell'installazione di SharePoint Server.  
  
 Quando si distribuisce un'applicazione SharePoint, il contenuto della cartella mappata e tutte le relative sottocartelle vengono copiati dal pacchetto della soluzione \(.wsp\) nel server che sta eseguendo SharePoint, in corrispondenza del percorso specificato nell'albero di cartelle di SharePoint.  Questo percorso è determinato dalla proprietà **Deployment Location** impostata per la cartella mappata.  Tutte le sottocartelle nella cartella mappata si riferiscono a **Deployment Location**.  Notare che la proprietà **Deployment Location**, non il nome della cartella mappata, determina dove vengono distribuiti gli elementi.  
  
 Le cartelle mappate possono essere aggiunte a un progetto utilizzando i relativi comandi dalla barra dei menu o dal menu di scelta rapida per il progetto.  È possibile utilizzare i comandi **Aggiungi cartella mappata "Immagini" SharePoint** e **Aggiungi cartella "Layout" SharePoint** per aggiungere queste cartelle mappate utilizzate più frequentemente.  È possibile eseguire il mapping di tutte le altre cartelle disponibili di SharePoint al progetto utilizzando il comando **Aggiungi cartella mappata di SharePoint** dal menu di scelta rapida e specificando le cartelle nella finestra di dialogo **Aggiungi cartella mappata di SharePoint**.  
  
## Aggiunta di cartelle mappate al progetto  
 Nella procedura riportata di seguito viene illustrato come aggiungere due cartelle mappate ad un progetto visual web part.  Per iniziare, creare un progetto visual web part.  
  
#### Per aggiungere cartelle mappate al progetto  
  
1.  Sulla barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto**, espandere il nodo **Visual Basic** o **Visual C\#**, espandere **Office\/SharePoint** e quindi selezionare il nodo **Soluzioni SharePoint**.  
  
3.  Nell'elenco di modelli di progetto, selezionare il modello **SharePoint 2013 Visual Web Part**.  
  
4.  Nella casella **Nome** inserire TestProject1 quindi scegliere il pulsante **OK**.  
  
5.  In **Personalizzazione guidata SharePoint**, scegliere il pulsante **Fine** per mantenere le impostazioni predefinite.  
  
6.  In **Esplora soluzioni** scegliere il nodo del progetto, quindi **Progetto**, **Aggiungi cartella mappata "Immagini" di SharePoint** dalla barra dei menu.  
  
     Nel progetto viene visualizzata una cartella denominata **Immagini** contenente una sottocartella denominata TestProject1.  Questa cartella mappata conterrà le immagini per il progetto visual web part.  
  
7.  In **Esplora soluzioni** scegliere il nodo del progetto, quindi scegliere **Progetto**, **Aggiungi cartella mappata di SharePoint** dalla barra dei menu per visualizzare la finestra di dialogo **Aggiungi cartella mappata di SharePoint**.  
  
8.  Nella visualizzazione ad albero delle cartelle disponibili per il mapping, scegliere la cartella **Risorse** quindi selezionare il pulsante **OK**.  
  
     Nel progetto viene visualizzata una cartella denominata **Risorse**.  Questa cartella può memorizzare elementi quali file di risorse sotto forma di stringa.  Le sottocartelle possono essere utili per l'organizzazione del contenuto di una cartella mappata, ma non vengono create automaticamente quando si aggiunge una cartella mappata tramite il comando **Aggiungi cartella mappata di SharePoint**.  Per aggiungere una sottocartella, scegliere la cartella **Risorse** quindi **Progetto**, **Nuova cartella** dalla barra dei menu.  
  
## Modifica del percorso di distribuzione di una cartella mappata  
 Per impostazione predefinita, le cartelle mappate vengono aggiunte in percorsi specifici sulla base del percorso di installazione radice dei SharePoint, indicato dal token {SharePointRoot}.  Tuttavia, questo percorso può essere modificato cambiando la proprietà **Deployment location** della cartella mappata.  Per ogni cartella mappata è prevista una proprietà **Deployment location** specifica.  
  
#### Per modificare il percorso di distribuzione di una cartella mappata  
  
1.  Scegliere una cartella mappata nel progetto creato precedentemente.  
  
2.  Nella finestra **Proprietà** selezionare il pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.png "Ellisse di ASP.NET Mobile Designer")\) dalla proprietà **Deployment location**.  
  
3.  Nella finestra di dialogo **Aggiungi cartella mappata di SharePoint** individuare la cartella a cui si desidera che punti la cartella mappata.  
  
4.  Scegliere il nodo, quindi fare clic sul pulsante **OK**.  
  
## Ridenominazione o rimozione di cartelle mappate  
  
#### Per rinominare o rimuovere una cartella mappata  
  
1.  Scegliere una cartella mappata nel progetto creato precedentemente.  
  
2.  Per rinominare la cartella mappata, aprire il relativo menu di scelta rapida, selezionare **Rinomina**, immettere il nuovo nome, quindi premere il pulsante Invio.  
  
     In alternativa, è possibile scegliere la cartella mappata che si desidera rinominare, aprire la finestra **Proprietà** quindi impostare il valore della proprietà **Folder name** con il nuovo nome.  
  
3.  Per rimuovere una cartella mappata dal progetto, aprire il relativo menu di scelta rapida, selezionare **Elimina**, quindi fare clic sul pulsante **OK** nella finestra di dialogo per confermarne la rimozione.  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  