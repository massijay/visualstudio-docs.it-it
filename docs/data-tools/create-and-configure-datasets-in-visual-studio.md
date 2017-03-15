---
title: "Procedura: creare un dataset tipizzato | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
helpviewer_keywords: 
  - "dataset [Visual Basic], creazione"
  - "dataset tipizzati, creazione"
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 36
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare un dataset tipizzato
Per creare un oggetto <xref:System.Data.DataSet> tipizzato si utilizza la **Configurazione guidata origine dati** oppure [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
> [!NOTE]
>  Per informazioni sulla creazione di dataset a livello di codice, vedere [Creazione di un DataSet](../Topic/Creating%20a%20DataSet.md).  
  
## Creazione di dataset tipizzati con la Configurazione guidata origine dati o con Progettazione DataSet  
  
#### Per creare un dataset con la Configurazione guidata origine dati  
  
1.  Dal menu **Dati** scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
2.  Selezionare **Database** nella pagina **Seleziona un tipo di origine dati**.  
  
3.  Completare la procedura guidata. Al progetto verrà aggiunto un dataset tipizzato.  Per ulteriori informazioni, vedere [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
#### Per creare un dataset con Progettazione DataSet  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  Selezionare **DataSet** dalla finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Digitare un nome per il dataset.  
  
4.  Scegliere **Aggiungi**.  
  
     Il dataset viene aggiunto al progetto e aperto in **Progettazione DataSet**.  
  
5.  Trascinare gli elementi dalla scheda **DataSet** della **Casella degli strumenti** nella finestra di progettazione.  Per ulteriori informazioni, vedere [Procedura: modificare un dataset](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
     In alternativa  
  
     Trascinare degli elementi da una connessione attiva in **Esplora server**\/**Esplora database** nella finestra **Progettazione DataSet**.  
  
## Vedere anche  
 [Procedura dettagliata: connessione ai dati in un database \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Procedura: modificare un dataset](../Topic/How%20to:%20Edit%20a%20Dataset.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Relazioni nei dataset](../data-tools/relationships-in-datasets.md)   
 [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)