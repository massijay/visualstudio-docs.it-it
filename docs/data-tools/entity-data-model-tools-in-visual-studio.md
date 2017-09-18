---
title: "Strumenti di ADO.NET Entity Data Model | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 21
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Strumenti di ADO.NET Entity Data Model
Gli strumenti di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] sono progettati per facilitare la compilazione delle applicazioni di [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].  È possibile trovare la documentazione completa per gli strumenti di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] in: [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/it-it/91076853-0881-421b-837a-f582f36be527).  
  
 Gli Strumenti di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] consentono di creare un *modello concettuale* da un database esistente, quindi di visualizzarlo graficamente e modificarlo.  Oppure, è possibile prima creare graficamente un modello concettuale, quindi generare un database che supporti il modello.  In entrambi i casi, è possibile aggiornare automaticamente il modello quando il database sottostante modifica e genera automaticamente codice del livello di oggetti per l'applicazione.  La generazione del database e la generazione di codice del livello di oggetti sono personalizzabili.  
  
 Nell'elenco riportato di seguito vengono descritti gli strumenti specifici che costituiscono gli Strumenti Entity Data Model:  
  
-   La finestra di progettazione [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] \(Entity Designer\) consente di creare visivamente e modificare entità, associazioni, mapping e relazioni di ereditarietà.  Entity Designer genera inoltre codice del livello di oggetti di [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
-   La procedura guidata di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] consente di generare un modello concettuale da un database esistente e aggiunge informazioni sulla connessione del database all'applicazione.  
  
-   La procedura guidata Crea database consente prima di creare un modello concettuale, quindi di creare un database che supporti il modello.  
  
-   La procedura guidata Aggiorna modello consente di aggiornare il modello concettuale, il modello di archiviazione e i mapping dopo aver apportato modifiche al database sottostante.  
  
    > [!NOTE]
    >  A partire da Visual Studio 2010, gli Strumenti di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] non supportano [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].  
  
 Gli strumenti generano o modificano un file .edmx contenente informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra i due modelli.  Per ulteriori informazioni, vedere [.edmx File Overview](http://msdn.microsoft.com/it-it/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
 È disponibile inoltre uno strumento da riga di comando progettato per sviluppare applicazioni che utilizzano un modello EDM: lo strumento EdmGen.exe.  Questo strumento può generare un modello concettuale, convalidare un modello esistente, produrre file del codice sorgente contenenti classi di oggetti basate sul modello concettuale e produrre file del codice sorgente contenenti visualizzazioni generate dal modello.  Per informazioni dettagliate su questo strumento della riga di comando, vedere [Generatore EDM \(EdmGen.exe\)](../Topic/EDM%20Generator%20\(EdmGen.exe\).md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[ADO.NET Entity Framework](../Topic/ADO.NET%20Entity%20Framework.md)|Viene descritto come utilizzare gli Strumenti di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], forniti da [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)], per creare applicazioni.|  
|[Entity Data Model](../Topic/Entity%20Data%20Model.md)|Fornisce collegamenti e informazioni per l'utilizzo di dati utilizzati dalle applicazioni compilate in [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|