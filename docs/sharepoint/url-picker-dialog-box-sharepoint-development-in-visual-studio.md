---
title: "Finestra di dialogo di selezione URL (sviluppo per SharePoint in Visual Studio)"
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
  - "VS.SharePointTools.VWD.URLPicker"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, finestra di progettazione"
  - "sviluppo per SharePoint in Visual Studio, Selezione URL"
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Finestra di dialogo di selezione URL (sviluppo per SharePoint in Visual Studio)
  Nella finestra di dialogo di selezione URL è possibile selezionare file come file di pagina master o file di immagine, contenuti nel progetto o nel server SharePoint locale.  
  
 Questa finestra di dialogo viene visualizzata se è possibile scegliere un file per impostare una proprietà.  È possibile aprire tale finestra di dialogo facendo clic sul pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\) accanto alle varie proprietà nella finestra **Proprietà**.  Il pulsante con i puntini di sospensione viene visualizzato anche come un prompt IntelliSense quando si assegnano valori a determinati attributi nella visualizzazione **Origine** della finestra di progettazione.  
  
## Elenco UIElement  
 **Cartelle di progetto**  
 Visualizza un elenco delle cartelle definite nel progetto o nel server che SharePoint sta eseguendo.  Fare clic sul pulsante di espansione per visualizzare le sottocartelle.  
  
 Espandere il nodo **Progetto** per selezionare i file nel progetto.  Per essere visualizzati come selezionabili nella finestra di dialogo, i file del progetto devono soddisfare i criteri riportati di seguito:  
  
-   Il file deve essere contenuto in una cartella mappata.  
  
-   Il file deve essere aggiunto al pacchetto della soluzione.  
  
-   Il file non si deve trovare in un altro progetto.  
  
 Se si desidera fare riferimento a file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.  
  
 Espandere il nodo **Server** per scegliere i file che si trovano sul server locale che esegue SharePoint.  Per essere visualizzati come selezionabili nella finestra di dialogo, tali file devono soddisfare i criteri riportati di seguito:  
  
-   Il file si deve trovare in una delle seguenti cartelle mappate: **Immagini**, **Layout** o **ControlTemplate**.  
  
-   Il file non si deve trovare nel database del contenuto di SharePoint.  
  
 Se si desidera fare riferimento a file che non soddisfano questi criteri, è necessario immettere manualmente il percorso del file.  
  
 **Contenuto della cartella**  
 Consente di visualizzare un elenco di file contenuti nella cartella selezionata.  Selezionare un file e fare clic su **OK** per chiudere la finestra di dialogo e inviare il file selezionato al processo che ha effettuato la chiamata.  
  
 **Tipo file**  
 Consente di effettuare la selezione da un elenco di file appropriati per l'attività in esecuzione.  
  
## Vedere anche  
 [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Visual Studio Web Development Content Map](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539)  
  
  