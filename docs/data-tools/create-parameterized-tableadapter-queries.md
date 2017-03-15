---
title: "Procedura: creare query TableAdapter con parametri | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "dati [Visual Studio], ricerca di dati"
  - "dati [Visual Studio], TableAdapters"
  - "query [Visual Studio], creazione"
  - "query [Visual Studio], TableAdapters"
  - "TableAdapters, query con parametri"
  - "TableAdapters, ricerca di dati"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare query TableAdapter con parametri
Una query con parametri restituisce dati che soddisfano le condizioni di una clausola WHERE all'interno della query.  Ad esempio, è possibile aggiungere un parametro a un elenco di clienti in modo da visualizzare solo i clienti di una determinata città aggiungendo `WHERE City = @City` alla fine dell'istruzione SQL che restituisce un elenco di clienti.  
  
 La creazione di query TableAdapter con parametri avviene in [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md) oppure durante la creazione di form con associazione a dati di un'applicazione Windows mediante il comando **Origine dati con parametri** del menu **Dati**.  Il comando **Origine dati con parametri** consente anche di creare controlli nel form per l'immissione di valori di parametro e l'esecuzione della query.  Per altre informazioni, vedere [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
> [!NOTE]
>  Per la costruzione di una query con parametri, usare la notazione di parametro specifica del database usato per la codifica.  Ad esempio, nelle origini dati Access e OleDb viene usato il punto interrogativo \(?\) per indicare i parametri, quindi la clausola WHERE risulterebbe simile a `WHERE City = ?`.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Creazione di una query TableAdapter con parametri  
  
#### Per creare una query con parametri in Progettazione DataSet  
  
-   Creare un nuovo oggetto TableAdapter aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.  Per altre informazioni, vedere [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
     \-oppure\-  
  
-   Aggiungere una query a un oggetto TableAdapter esistente aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.  Per altre informazioni, vedere [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### Per creare una query con parametri durante la progettazione di un form associato a dati  
  
1.  Selezionare un controllo nel form che sia già associato a un dataset.  Per altre informazioni, vedere [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Nel menu **Dati** scegliere **Aggiungi query**.  
  
3.  Inserire i dati mancanti nella finestra di dialogo **Generatore di criteri per la ricerca** aggiungendo all'istruzione SQL una clausola WHERE con i parametri desiderati.  Per altre informazioni, vedere [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Vedere anche  
 [TableAdapters](../Topic/TableAdapters.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)