---
title: "Extending the SharePoint Project System"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  È possibile creare soluzioni SharePoint tramite un set di modelli di progetto e modelli di elemento in Visual Studio.  Questi modelli soddisfano i requisiti di molti scenari di sviluppo, ma è possibile individuare alcuni casi in cui non viene garantita la funzionalità richiesta.  In questi casi, è possibile estendere il sistema di progetto SharePoint.  
  
## Panoramica del sistema del progetto SharePoint  
 Il sistema del progetto SharePoint si basa sul componente fondamentale degli *elementi di progetto SharePoint*.  Un elemento di progetto SharePoint rappresenta una singola personalizzazione di SharePoint, ad esempio una definizione di elenco, una web part o un tipo di contenuto.  
  
 Un progetto SharePoint è un progetto di Visual Studio che include uno o più elementi di progetto SharePoint.  I progetti SharePoint contengono inoltre altri componenti che definiscono la modalità di raggruppamento degli elementi di progetto in funzionalità e pacchetti per la distribuzione.  
  
 Per ulteriori informazioni sul contenuto degli elementi di progetto SharePoint, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Estensione del sistema di progetto SharePoint  
 Tale estensione può essere effettuata nei modi seguenti:  
  
-   Definire i tipi di elemento di progetto SharePoint personalizzati e associarli ai nuovi modelli di elemento o di progetto in Visual Studio.  È ad esempio possibile definire un tipo di elemento di progetto SharePoint per la creazione di un'azione o un campo personalizzato.  Per ulteriori informazioni, vedere [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Estendere i tipi di elemento di progetto SharePoint già installati in Visual Studio.  Ad esempio, è possibile aggiungere una voce di menu di scelta rapida a un elemento di progetto in **Esplora soluzioni** e personalizzare l'elemento di progetto quando uno sviluppatore sceglie la voce di menu.  Per ulteriori informazioni, vedere [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Estendere i progetti SharePoint.  Ad esempio è possibile aggiungere gestori eventi per effettuare attività specifiche quando gli elementi vengono aggiunti o sono rimossi dai progetti SharePoint.  Per ulteriori informazioni, vedere [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md).  
  
-   Estendere il comportamento di distribuzione e creazione di pacchetti degli elementi di progetto SharePoint e dei progetti SharePoint.  Ad esempio è possibile creare passaggi di distribuzione personalizzati da eseguire quando si distribuisce o ritrae un progetto oppure è possibile effettuare attività personalizzate aggiuntive quando vengono eseguiti determinati passaggi di distribuzione in Visual Studio.  Per ulteriori informazioni, vedere [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## Attività di sviluppo comuni  
 È possibile eseguire le seguenti attività comuni nelle estensioni del sistema di progetto SharePoint:  
  
-   Salvare i dati in formato stringa personalizzati con gli elementi di progetto e in diversi tipi di file di progetto.  Per ulteriori informazioni, vedere [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Conversione di un oggetto nel sistema del progetto SharePoint in un oggetto corrispondente nel modello a oggetti di automazione o di integrazione di Visual Studio o viceversa.  Per ulteriori informazioni, vedere [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## Vedere anche  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  