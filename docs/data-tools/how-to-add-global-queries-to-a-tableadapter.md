---
title: "Procedura: aggiungere query globali a un dataset | Microsoft Docs"
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
  - "dati [Visual Studio], TableAdapters"
  - "dataset [Visual Basic], funzioni globali"
  - "dataset [Visual Basic], funzioni scalari"
  - "funzioni globali, dataset"
  - "query [Visual Studio], TableAdapters"
  - "funzioni scalari, dataset"
  - "TableAdapter (query)"
  - "TableAdapter (query, configurazione guidata)"
  - "TableAdapters, query globali"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: aggiungere query globali a un dataset
Vengono dette *query globali* le query SQL che restituiscono un singolo valore \(scalare\) o nessun valore.  Generalmene le funzioni globali eseguono operazioni sui database, quali inserimenti, aggiornamenti ed eliminazioni, e l'aggregazione di informazioni, come la restituzione del numero di clienti inclusi in una tabella o il costo totale di tutti gli elementi inclusi in un determinato ordine.  
  
 Per aggiungere query globali, eseguire la **Configurazione guidata query TableAdapter** dall'interno di **Progettazione DataSet**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per aggiungere una query globale a un dataset  
  
1.  Aprire un dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Trascinare una **Query** dalla scheda **DataSet** della **Casella degli strumenti** in un'area vuota di **Progettazione DataSet**.  
  
     Verrà visualizzata la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md).  
  
3.  Selezionare una connessione per la query.  È possibile selezionarne una dall'elenco oppure crearne una nuova.  Se si crea una nuova connessione, sarà possibile salvarla nel file di configurazione dell'applicazione.  Per ulteriori informazioni, vedere [Procedura: salvare e modificare stringhe di connessione](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
4.  Scegliere se si desidera utilizzare istruzioni SQL o stored procedure.  
  
5.  Scegliere la stored procedure da utilizzare oppure, nella pagina **Scegli tipo di query** della procedura guidata, scegliere il tipo di query desiderato e fare clic su **Avanti**.  
  
6.  Fornire una query che esegue l'attività desiderata, ad esempio `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Trascinando una query direttamente in **Progettazione DataSet** è possibile creare un metodo che restituirà solo un valore scalare \(singolo\).  Sebbene attraverso la query o la stored procedure selezionata possa essere restituito più di un valore singolo, il metodo creato dalla procedura guidata restituirà solo un valore singolo.  La query potrebbe ad esempio restituire la prima colonna della prima riga dei dati ottenuti.  
  
7.  Completare la procedura guidata. La query verrà aggiunta a **Progettazione DataSet**.  Per ulteriori informazioni sull'esecuzione delle query, vedere [Procedura: esecuzione di query TableAdapter](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md).  
  
## Vedere anche  
 [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Procedura: esplorare i dati con il controllo BindingNavigator Windows Form](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)