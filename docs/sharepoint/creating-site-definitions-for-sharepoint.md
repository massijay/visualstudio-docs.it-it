---
title: "Creazione di definizioni di sito per SharePoint"
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
  - "sviluppo per SharePoint in Visual Studio, definizioni di sito"
  - "definizioni di sito [sviluppo per SharePoint in Visual Studio]"
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Creazione di definizioni di sito per SharePoint
  Il progetto Definizione di sito di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di creare una *definizione di sito* che viene utilizzata come base per un nuovo sito di SharePoint.  Queste definizioni non consentono solo di determinare l'aspetto e il comportamento del sito di SharePoint, bensì anche il contenuto predefinito e la funzionalità.  Nella definizione è possibile inserire elenchi preconfigurati, tipi di contenuto, ricevitori di eventi, immagini e altri elementi.  SharePoint include alcune definizioni di sito come BLOG, ad esempio.  In un sito creato in base alla definizione di sito BLOG sono contenuti gli elenchi, le web part e altri elementi richiesti da un sito blog.  
  
 Per ulteriori informazioni sulle definizioni di sito, vedere [Modelli di sito e definizioni](http://go.microsoft.com/fwlink/?LinkId=179134).  
  
## Progetti di definizione di sito  
 Nei progetti di definizione di sito di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sono disponibili solo i file di base necessari a un sito di SharePoint e nessuna funzionalità predefinita.  Per ottenere la funzionalità desiderata è necessario aggiungere file e contenuti.  Il sito può essere compilato manualmente creando e aggiungendo i file necessari.  
  
## Associazione delle funzionalità  
 Un vantaggio della creazione di definizioni di sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] è l'utilizzo automatico dell'*associazione delle funzionalità*.  L'associazione delle funzionalità consente di collegare una funzionalità a una definizione di sito anziché incorporare la funzionalità nella definizione di sito stessa.  In questo modo è possibile aggiungere la funzionalità a qualsiasi sito creato tramite la relativa definizione senza modificare la definizione di sito originale.  Per ulteriori informazioni, vedere [Associazione delle funzionalità](http://go.microsoft.com/fwlink/?LinkID=119283).  
  
## Componenti del progetto di definizione di sito  
 Quando si crea una soluzione di definizione di sito, i seguenti file predefiniti vengono aggiunti al nodo **SiteDefinition**.  
  
|Nome file|Descrizione|  
|---------------|-----------------|  
|default.aspx|Home page ASPX predefinita per il nuovo sito di SharePoint.|  
|onet.xml|Vengono specificati la configurazione del nuovo sito, i componenti del modello di definizione di sito e il comportamento predefinito.  In queste impostazioni possono essere inclusi attributi come i tipi di contenuto abilitati, le visualizzazioni elenco predefinite, i file del modello di documento e le web part incluse nel sito.  Per impostazione predefinita, nella sezione `Modules` sono elencati i file da aggiungere al sito di SharePoint e la modalità di configurazione.|  
|webtemp\_*SiteDefinitionName*.xml|Specifica le configurazioni di definizioni di sito visualizzate nella sezione **Selezione modello** della pagina **Nuovo sito di SharePoint**.|  
  
 Per impostazione predefinita, tutte le definizioni di sito vengono archiviate nella cartella presente in *drive:*\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\14\\TEMPLATE\\SiteTemplates.  In ogni definizione di sito è disponibile una sottocartella.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura dettagliata: Creare un progetto di definizione di sito di base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Viene illustrata in modo dettagliato la creazione di un progetto di definizione di sito di base in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Come creare una definizione e una configurazione personalizzata di un sito](http://go.microsoft.com/fwlink/?LinkId=183309)|Viene descritto come creare una definizione di sito personalizzata in SharePoint copiando una definizione di sito esistente e modificando la copia.|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|Viene descritto il file originale che consente di specificare le definizioni di sito disponibili nella sezione **Selezione modello** della pagina **Nuovo sito di SharePoint**.|  
|[Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Viene descritto come preparare le soluzioni SharePoint per utilizzo globale.|  
|[Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Viene descritto come creare le parti di una pagina di SharePoint che gli utenti possono modificare.|  
|[Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Viene descritto come creare i controlli riutilizzabili che vengono eseguiti nelle pagine dell'applicazione e nelle web part.|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|Viene descritto come utilizzare la finestra di progettazione visualizzata quando si apre una pagina Web nel progetto.|  
|[Cenni preliminari sulle pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178726)|Vengono fornite informazioni generali sulla struttura delle pagine Web [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], viene descritta l'elaborazione delle pagine in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] e viene illustrato il modo in cui il markup visualizzato nelle pagine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] è conforme agli standard XHTML.|  
|[Panoramica della sintassi delle pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178727)|Vengono descritti gli elementi di markup che costituiscono una pagina ASP.NET.|  
|[Programmazione di pagine Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=178728)|Vengono fornite informazioni sulla creazione dei gestori di eventi in [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] e sull'utilizzo di script client.|  
|[Programmazione di Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=178729)|Viene descritto come utilizzare il modello a oggetti gestito fornito in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)].|  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  