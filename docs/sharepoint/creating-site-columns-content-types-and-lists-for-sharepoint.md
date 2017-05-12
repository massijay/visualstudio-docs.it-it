---
title: "Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint"
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
  - "VS.SharePointTools.ListDesigner.ContentTypeSetting"
  - "VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ListDesigner.CreatingLists"
  - "VS.SharePointTools.ListDesigner.ListPage"
  - "VS.SharePointTools.ListDesigner.ViewPage"
  - "VS.SharePointTools.ListDesigner.CommonPropertiesPage"
  - "VS.SharePointTools.ContentTypeDesigner.ColumnsPage"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 9ceed263-3aec-41dc-8708-63cb37a08fa8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint
  Visual Studio fornisce modelli di elementi di progetto per svariati elementi fondamentali di SharePoint, inclusi *elenchi* e *tipi di contenuto*, entrambi i quali possono includere le colonne del sito \(o i *campi*\).  Le finestre di progettazione per i tipi di contenuto e gli elenchi semplificano come non mai la creazione di questi elementi.  
  
## Colonne del sito  
 Le colonne del sito sono uno degli elementi elementari che possono essere aggiunti ad un progetto SharePoint.  Una colonna del sito rappresenta un tipo di dato, come un numero di telefono, un commento, o il nome della città di un contatto in un elenco di contatti.  
  
 Il nuovo modello dell'elemento colonna del sito di un progetto rende la creazione delle colonne del sito più semplici rispetto le versioni precedenti di Visual Studio.  Dopo aver creato una nuova colonna del sito, è possibile modificare l'XML nel file di colonna del sito Elements.xml per includere le informazioni desiderate, ad esempio il nome visualizzato, il tipo di dati e il gruppo nel quale si desidera che la colonna del sito venga visualizzata in SharePoint.  Per ulteriori informazioni sulle colonne del sito, vedere [Introduzione alle colonne](http://go.microsoft.com/fwlink/?LinkId=224996).  
  
## Tipi di contenuto ed elenchi  
 I tipi di contenuto e gli elenchi sono tra gli elementi più frequentemente utilizzati in SharePoint.  
  
 Un tipo di contenuto definisce i meta dati, il flusso di lavoro e il comportamento di una categoria di elementi in un elenco di SharePoint o in una raccolta documenti.  Ad esempio, è possibile creare un tipo di contenuto per le informazioni in una lista di contatti o in un elenco dell'attività.  Un tipo di contenuto del contatto potrebbe includere le colonne come il Nome, l'Email, il Numero di telefono e l'Indirizzo.  Un tipo di contenuto definito a livello di sito è indipendente da qualsiasi elenco o raccolta documenti nel sito.  È possibile utilizzare lo stesso tipo di contenuto con diversi elenchi o raccolte documenti sul sito SharePoint.  È inoltre possibile utilizzare diversi tipi di contenuto nello stesso elenco o raccolta documenti.  
  
 Un elenco è una raccolta di informazioni in SharePoint da condividere con altri utenti.  Gli elenchi sono costituiti da righe di colonne che contengono i dati.  Alcuni esempi di elenchi includono: un elenco delle attività, dei contatti e degli annunci.  
  
 Le finestre di progettazione dell'elenco e il tipo di contenuto in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rendono la creazione dei tipi di contenuto e delle liste più facili e intuitive rispetto precedenti versioni di Visual Studio.  L'interfaccia utente consente di creare visivamente i tipi di contenuto e gli elenchi in modo comune, consentendo di ordinare e raggruppare i dati in elenchi e utilizzare il raggruppamento delle intestazioni.  Per ulteriori informazioni sui tipi di contenuto, vedere [Tipi di contenuto](http://go.microsoft.com/fwlink/?LinkId=224997).  Per ulteriori informazioni sugli elenchi, vedere [Moduli elenco](http://go.microsoft.com/fwlink/?LinkId=224998) ed [Visualizzazioni elenco](http://go.microsoft.com/fwlink/?LinkId=224999).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Viene illustrato come creare colonne del sito che utilizzano un tipo di contenuto personalizzato.  Il tipo di contenuto viene quindi utilizzato in un elenco personalizzato.|  
  
## Vedere anche  
 [Iniziare lo sviluppo di SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=225000)  
  
  