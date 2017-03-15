---
title: "Procedura: separare dataset e TableAdapter in progetti diversi | Microsoft Docs"
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
  - "applicazioni a più livelli, separazione di dataset e TableAdapter"
  - "TableAdapters, applicazioni a più livelli"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: separare dataset e TableAdapter in progetti diversi
I dataset tipizzati sono stati migliorati in modo da poter generare i [TableAdapters](../Topic/TableAdapters.md) e le classi di dataset in progetti separati  consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.  
  
 Nella procedura descritta di seguito viene illustrato l'utilizzo di [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) per generare il codice del dataset in un progetto separato da quello che contiene il codice del `TableAdapter` generato.  
  
## Separazione di dataset e TableAdapter  
 Quando si separa il codice del dataset dal codice del `TableAdapter`, il progetto che conterrà il codice del dataset deve risiedere nella soluzione corrente.  Se questo progetto non risiede nella soluzione corrente, non sarà disponibile nell'elenco **Progetto DataSet** della finestra **Proprietà**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per separare il dataset in un progetto diverso  
  
1.  Aprire una soluzione contenente un dataset \(file xsd\).  
  
    > [!NOTE]
    >  Se la soluzione non contiene il progetto in cui si desidera separare il codice del dataset, è necessario crearlo oppure aggiungere un progetto esistente alla soluzione.  
  
2.  Fare doppio clic su un file del dataset tipizzato \(file xsd\) in **Esplora soluzioni** per aprire il dataset in **Progettazione DataSet**.  
  
3.  Fare clic su un'area vuota di **Progettazione DataSet**.  
  
4.  Individuare il nodo **Progetto DataSet** nella finestra **Proprietà**.  
  
5.  Nell'elenco **Progetto DataSet** fare clic sul nome del progetto in cui si desidera generare il codice del dataset.  
  
     Dopo avere fatto clic sul progetto in cui generare il codice del dataset, la proprietà **File DataSet** viene popolata con un nome file predefinito.  Se necessario, è possibile modificare questo nome.  Inoltre, se si desidera generare il codice del dataset in una directory specifica, è possibile impostare la proprietà **Cartella del progetto** sul nome di una cartella.  
  
    > [!NOTE]
    >  Quando si separano i dataset e i TableAdapter impostando la proprietà **Progetto DataSet**, le classi del dataset parziale presenti nel progetto non verranno spostate automaticamente.  Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
6.  Salvare il dataset.  
  
     Il codice del dataset viene generato nel progetto selezionato nella proprietà **Progetto DataSet** e il codice del **TableAdapter** viene generato nel progetto corrente.  
  
 Per impostazione predefinita, dopo avere separato il codice del dataset e il codice del `TableAdapter`, il risultato sarà un file di classe discreto in ogni progetto.  Nel progetto originale sarà presente un file denominato NomeDataset.Designer.vb o NomeDataset.Designer.cs contenente il codice `TableAdapter`.  Nel progetto definito nella proprietà **Progetto DataSet** sarà presente un file denominato NomeDataset.DataSet.Designer.vb o NomeDataset.DataSet.Designer.cs contenente il codice del dataset.  
  
> [!NOTE]
>  Selezionare il progetto del dataset o del `TableAdapter` e fare clic su **Mostra tutti i file** in **Esplora soluzioni** per visualizzare il file di classe generato.  
  
## Vedere anche  
 [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)