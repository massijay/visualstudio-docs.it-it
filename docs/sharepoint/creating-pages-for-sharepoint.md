---
title: "Creazione di pagine per SharePoint"
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
helpviewer_keywords: 
  - "pagine contenuto [sviluppo per SharePoint in Visual Studio], progettazione"
  - "pagine master [sviluppo per SharePoint in Visual Studio], progettazione"
  - "layout di pagina [sviluppo per SharePoint in Visual Studio], progettazione"
  - "sviluppo per SharePoint in Visual Studio, pagine contenuto"
  - "sviluppo per SharePoint in Visual Studio, pagine master"
  - "sviluppo per SharePoint in Visual Studio, layout di pagina"
ms.assetid: 57678ed1-841f-45de-a1d3-5f9e233bf3ce
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Creazione di pagine per SharePoint
  È possibile creare pagine applicazione, pagine del sito, pagine master e layout di pagina per un sito di SharePoint.  
  
 È possibile creare pagine applicazione utilizzando un modello in Visual Studio.  Creare pagine del sito, pagine master e layout di pagina utilizzando SharePoint Designer.  Successivamente è possibile importare queste pagine in Visual Studio per utilizzarle in un progetto SharePoint.  
  
 È possibile modificare inoltre l'aspetto e il comportamento delle pagine tramite fogli di stile CSS, ECMAScript e temi.  
  
## Tipi di pagine di SharePoint  
 Nella tabella riportata di seguito vengono descritti i quattro tipi principali di pagine contenuti in un sito di SharePoint.  
  
|Tipo di pagina|Descrizione|  
|--------------------|-----------------|  
|Pagine applicazione|Creare una pagina applicazione se si desidera includervi codice personalizzato o se si desidera che la pagina venga condivisa tra più siti.  Negli altri casi, una pagina del sito potrebbe essere la scelta migliore.|  
|Pagine del sito|Creare una pagina del sito se si desidera eseguire una qualsiasi delle attività riportate di seguito.<br /><br /> -   Aggiungere la pagina a una libreria di SharePoint.<br />-   Abilitare la pagina per includere funzionalità quali Web part dinamiche e aree Web part.<br />-   Consentire agli utenti di personalizzare la pagina tramite SharePoint Designer.<br /><br /> Non creare una pagina del sito se si desidera che nella pagina siano contenuto codice personalizzato.  Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, tale codice non verrà più eseguito quando l'utente personalizzerà la pagina tramite SharePoint Designer.|  
|Pagine master|Creare una pagina master se si desidera definire una struttura comune per pagine del sito e pagine applicazione.|  
|Layout di pagina|I layout di pagina sono specifici di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] e consentono di definire ulteriormente una struttura comune per pagine del sito e pagine applicazione.|  
  
 Per una panoramica su ciascun tipo di pagina, vedere [Blocco di costruzione: Pagine e interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095) e [Layout di pagina e pagine master](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## Creazione di pagine applicazione  
 È possibile creare pagine applicazione in Visual Studio aggiungendo un elemento **Pagina applicazione** a un progetto SharePoint.  È possibile aggiungere controlli alla pagina e gestire gli eventi del controllo aggiungendo il codice relativo.  
  
 È possibile impostare punti di interruzione nel file di codice della pagina, avviare il debugger e testare la pagina su un sito di SharePoint locale senza eseguire ulteriori passaggi di configurazione.  Per ulteriori informazioni, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## Creazione di pagine del sito, pagine master e layout di pagina  
 È possibile creare pagine del sito, pagine master e layout di pagina utilizzando SharePoint Designer.  Quindi, è possibile importare queste pagine in Visual Studio.  Importare le pagine se si desidera sfruttare le funzionalità di distribuzione o controllo del codice sorgente disponibili in Visual Studio.  Per ulteriori informazioni, vedere [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Poiché la modifica di queste pagine dopo averle importate è un'operazione difficile, è necessario progettarle prima di importarle.  
  
## Creazione di fogli di stile CSS, ECMAScript e temi  
 Visual Studio non fornisce modelli per lo sviluppo di file di fogli di stile CSS, ECMAScript \(JavaScript, JScript\) o di temi per i siti di SharePoint.  È possibile creare questi file tramite le linee guida disponibili in SharePoint SDK o tramite strumenti quali SharePoint Designer.  
  
 È possibile aggiungere direttamente questi file alla soluzione oppure è possibile importarli.  In entrambi i casi, è necessario creare le cartelle mappate appropriate per ogni elemento che si aggiunge.  Per ulteriori informazioni sulla creazione di una cartella mappata, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Per ulteriori informazioni sulla creazione di fogli di stile CSS, vedere [Utilizzo della classe dei fogli di stile CSS in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098).  Per ulteriori informazioni sulla creazione di file JavaScript e JScript per una soluzione di SharePoint, vedere [Impostazione di una pagina ASPX di base per ECMAScript](http://go.microsoft.com/fwlink/?LinkID=182099).  Per ulteriori informazioni sui temi, vedere [Blocco di costruzione: Pagine e interfaccia utente](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)|Viene illustrato come aggiungere le pagine delle applicazioni, ovvero il contenuto con estensione aspx unito con una pagina master di SharePoint.|  
|[Procedura: creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)|Viene illustrato come creare pagine ASP.NET che verranno eseguite in un sito di SharePoint.|  
|[Procedura dettagliata: creazione di una pagina di un'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Viene illustrato come progettare una pagina Web ASP.NET per un sito di SharePoint ed eseguirne il debug.|  
|[Utilizzo di Visual Web Developer](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Viene descritto come utilizzare la finestra di progettazione visualizzata quando si apre una pagina Web nel progetto.|  
  
  