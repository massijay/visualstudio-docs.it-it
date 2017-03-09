---
title: "Procedura: aggiornare i dati mediante un TableAdapter | Microsoft Docs"
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
  - "dati [Visual Studio], salvataggio"
  - "dati [Visual Studio], TableAdapters"
  - "dati [Visual Studio], aggiornamento"
  - "salvataggio di dati"
  - "TableAdapters, aggiornamento di dati"
  - "aggiornamento di dati, TableAdapters"
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: aggiornare i dati mediante un TableAdapter
Dopo aver modificato e convalidato i dati del dataset in uso, è possibile inviare i dati aggiornati a un database.  A tale scopo, viene chiamato il metodo `Update` di un oggetto [TableAdapter](../data-tools/tableadapter-overview.md).  Il metodo `Update` dell'adattatore consente di aggiornare una tabella di dati singola e di eseguire il comando corretto \(INSERT, UPDATE o DELETE\) in base alla proprietà <xref:System.Data.DataRow.RowState%2A> di ciascuna riga di dati della tabella.  Quando si salvano i dati nelle tabelle correlate, Visual Studio fornisce un nuovo componente TableAdapterManager che consente di eseguire i salvataggi nell'ordine corretto in base ai vincoli di chiave esterna definiti nel database.  Per ulteriori informazioni, vedere [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Poiché il tentativo di aggiornare un'origine dati con il contenuto di un dataset può causare errori, è necessario immettere il codice che chiama il metodo `Update` dell'adattatore all'interno di un blocco `try`\/`catch`.  
  
 La procedura corretta per aggiornare un'origine dati può variare a seconda delle esigenze aziendali, ma l'applicazione dovrà comprendere i seguenti passaggi:  
  
1.  Chiamare il metodo `Update` dell'adattatore all'interno di un blocco `try`\/`catch`.  
  
2.  Se si intercetta un'eccezione, individuare la riga di dati che ha provocato l'errore.  Per ulteriori informazioni, vedere [Procedura: individuare righe con errori](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Risolvere il problema nella riga di dati, se possibile a livello di codice oppure presentando la riga non valida all'utente per la modifica, quindi tentare nuovamente l'aggiornamento \(proprietà <xref:System.Data.DataRow.HasErrors%2A>, metodo <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Salvataggio dei dati in un database  
 Chiamare il metodo `Update` di un TableAdapter, passando il nome della tabella di dati che contiene i valori da scrivere nel database.  
  
#### Per aggiornare un database con un dataset mediante un TableAdapter  
  
-   Racchiudere il metodo `Update` dell'adattatore all'interno di un blocco `try`\/`catch`.  Nell'esempio che segue viene illustrato un tentativo di aggiornamento dall'interno di un blocco `try`\/`catch` con il contenuto della tabella `Customers` nel dataset `NorthwindDataSet`.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]  
  
## Aggiornamento di due tabelle correlate di un dataset con un TableAdapter  
 Quando si aggiornano le tabelle correlate in un dataset, è necessario effettuare l'aggiornamento nella sequenza corretta, in modo da ridurre la possibilità di violare i vincoli di integrità referenziale.   L'ordine di esecuzione dei comandi seguirà anche gli indici dell'oggetto <xref:System.Data.DataRowCollection> nel dataset.  Per impedire che vengano generati errori di integrità dei dati, è preferibile aggiornare il database rispettando questa sequenza:  
  
1.  Tabella figlio: eliminare i record.  
  
2.  Tabella padre: inserire, aggiornare ed eliminare i record.  
  
3.  Tabella figlio: inserire e aggiornare i record.  
  
    > [!NOTE]
    >  Se è in corso l'aggiornamento di due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione.  Una transazione è un processo che garantisce il corretto inserimento di tutte le modifiche correlate in un database prima del relativo commit.  Per ulteriori informazioni, vedere [Transazioni e concorrenza](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Per aggiornare due tabelle correlate mediante un TableAdapter  
  
1.  Creare tre tabelle di dati  temporanee in cui collocare i diversi record.  
  
2.  Chiamare il metodo `Update` per ciascun sottoinsieme di righe da un blocco `try`\/`catch`.  Se si verificano errori di aggiornamento, interrompere il processo e risolverli.  
  
3.  Eseguire il commit delle modifiche nel database.  
  
4.  Eliminare le tabelle di dati temporanee per liberare le risorse.  
  
     Nell'esempio seguente viene illustrata la procedura per aggiornare un'origine dati con un dataset che contiene tabelle correlate.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_2.cs)]  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)