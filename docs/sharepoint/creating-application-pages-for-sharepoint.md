---
title: "Creazione di pagine applicazione per SharePoint | Microsoft Docs"
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
  - "pagine applicazione [sviluppo per SharePoint in Visual Studio], creazione"
  - "pagine applicazione [sviluppo per SharePoint in Visual Studio], sviluppo"
  - "sviluppo per SharePoint in Visual Studio, pagine applicazione"
  - "sviluppo per SharePoint in Visual Studio, pagine contenuto"
  - "sviluppo per SharePoint in Visual Studio, pagine Web"
ms.assetid: a6e97149-15dd-4bdb-8d75-3b53f886f76c
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Creazione di pagine applicazione per SharePoint
  Una *pagina applicazione* è una pagina Web ASP.NET progettata per essere utilizzata in un sito Web di SharePoint.  Le pagine applicazione sono un tipo specializzato di pagina ASP.NET.  La differenza principale tra una pagina applicazione e una pagina ASP.NET standard è costituita dal fatto che in una pagina applicazione è presente contenuto unito con una pagina master di SharePoint.  Una pagina master consente alle pagine applicazione di condividere lo stesso aspetto e lo stesso comportamento delle altre pagine di un sito.  
  
 In Visual Studio è possibile progettare pagine applicazione tramite una finestra di progettazione.  Nella finestra di progettazione viene visualizzata un'area di contenuto per ogni segnaposto del contenuto definito in una pagina master.  È possibile progettare la pagina applicazione mediante il trascinamento di controlli in queste aree di contenuto.  
  
## Pagine applicazione  
 Le pagine applicazione sono condivise da tutti i siti sul server, mentre una pagina di sito è specifica di un sito.  Per ulteriori informazioni [Tipi di pagina SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Per impostazione predefinita, la maggior parte delle pagine visualizzate quando si crea un sito di SharePoint sono pagine di sito.  È possibile aggiungere una pagina di sito a una raccolta pagine di SharePoint.  Gli utenti possono personalizzare una pagina di sito utilizzando strumenti quale SharePoint Designer.  In una pagina di sito possono inoltre essere incluse funzionalità quali web part dinamiche e aree web part.  
  
 Nelle pagine applicazione non possono essere effettuate queste operazioni.  Una pagina applicazione è tuttavia il tipo di pagina che è consigliabile creare se si desidera includervi codice personalizzato.  Anche se è possibile aggiungere codice personalizzato a una pagina di sito, tale codice non funzionerà più quando l'utente personalizza la pagina utilizzando strumenti quale SharePoint Designer.  
  
> [!NOTE]  
>  In Visual Studio non sono disponibili modelli che semplificano la creazione di pagine di sito per un sito di SharePoint.  Per ulteriori informazioni, vedere [Tipi di pagina SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## Creazione di una pagina applicazione  
 Per creare una pagina applicazione aggiungere un elemento **Pagina applicazione** a un progetto SharePoint.  Quando si crea una pagina applicazione, in Visual Studio vengono aggiunte al progetto le cartelle seguenti:  
  
|Cartella|Descrizione|  
|--------------|-----------------|  
|Layouts|Viene eseguito il mapping alla directory virtuale \_layouts del file system di SharePoint.|  
|Sottocartella di Layouts|Contiene i file che costituiscono la pagina applicazione.  Per impostazione predefinita, il nome di questa cartella è identico a quello del progetto.  È possibile rinominare questa cartella in qualsiasi momento.  Quando si esegue il progetto, questa cartella viene distribuita automaticamente alla directory virtuale \_layouts del file system di SharePoint.|  
  
 In Visual Studio vengono aggiunti al progetto i file seguenti:  
  
|File|Descrizione|  
|----------|-----------------|  
|File di pagina ASP.NET \(\*.aspx\)|Contiene il markup XML che definisce la pagina.|  
|File di codice della pagina applicazione|Contiene il code\-behind della pagina applicazione.  Aggiungere codice a questo file per gestire gli eventi.|  
|File di codice della finestra di progettazione della pagina applicazione|Contiene codice generato dalla finestra di progettazione.  Non modificare direttamente questo file.|  
  
## Progettazione e debug di una pagina applicazione  
 Per progettare il contenuto di una pagina applicazione, utilizzare la finestra di progettazione di Visual Web Developer in Visual Studio.  Questa finestra di progettazione viene visualizzata quando si apre la pagina applicazione nel progetto \(facendo doppio clic o aprendo il menu di scelta rapida e scegliendo **Apri**\).  Per ulteriori informazioni sull'utilizzo di questa finestra di progettazione, vedere [Visual Studio Web Development Content Map](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
> [!NOTE]  
>  È possibile progettare la pagina solo nella visualizzazione **Origine** della finestra di progettazione.  La visualizzazione **Progettazione** della finestra di progettazione è disabilitata per le pagine applicazione.  
  
 È possibile eseguire il debug di una pagina applicazione procedendo come per altri elementi di progetti SharePoint in Visual Studio.  Quando si avvia il debugger di Visual Studio, viene aperto il sito di SharePoint.  
  
 Per visualizzare la pagina applicazione, è necessario passare manualmente al percorso della pagina applicazione \(ad esempio: http:\/\/*Server\_Name*\/\_layouts\/*Project\_Name*\/ApplicationPage1.aspx\).  
  
 Per ulteriori informazioni sul debug di progetti SharePoint, vedere [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Scelta di una pagina master  
 Per impostazione predefinita, un elemento **Pagina applicazione** fa riferimento alla pagina master del sito utilizzato per eseguire il debug del progetto.  Tale pagina è denominata v4.master ed è elencata in **Raccolta pagine master** del sito di SharePoint.  
  
 È possibile modificare in modo esplicito la pagina master che verrà utilizzata dalla pagina applicazione impostando l'attributo `MasterPageFile` dell'elemento `Page` dell'applicazione. Ad esempio: `MasterPageFile="~/_layouts/applicationv4.master"`.  È infatti necessario impostare questo attributo se le pagine master dinamiche non sono abilitate sul server SharePoint.  Per ulteriori informazioni sulle pagine master in SharePoint, vedere [Pagine master](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## Vedere anche  
 [Sviluppo di SharePoint Foundation completo](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [Panoramica delle pagine Web ASP.NET](http://msdn.microsoft.com/library/52fa0455-41ea-4315-8208-2861d1527da2)   
 [Panoramica della sintassi delle pagine Web ASP.NET](http://msdn.microsoft.com/library/09074b20-ece9-46fa-bc8f-ab2595ed2c02)   
 [Programmazione di pagine Web ASP.NET](http://msdn.microsoft.com/it-it/5626c661-8057-4de8-b658-c2e35ed4b4c9)  
  
  