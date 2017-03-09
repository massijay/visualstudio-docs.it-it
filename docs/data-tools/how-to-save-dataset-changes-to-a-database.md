---
title: "Procedura: salvare le modifiche di un dataset in un database | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DbDataAdapter.Update"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], salvataggio"
  - "database, aggiornamento"
  - "aggiornamento di dataset, scrittura di modifiche nell'origine dati"
ms.assetid: c9970150-b71b-4c9d-a355-5efb6b510dca
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: salvare le modifiche di un dataset in un database
Dopo aver modificato e convalidato i dati del dataset in uso, è possibile inviare i dati aggiornati a un database.  Per eseguire questa operazione, chiamare il metodo `Update` di un oggetto [TableAdapter](../data-tools/tableadapter-overview.md) o adattatore dati.  Il metodo `Update` dell'adattatore consente di aggiornare una tabella di dati singola e di eseguire il comando corretto \(INSERT, UPDATE o DELETE\) in base alla proprietà <xref:System.Data.DataRow.RowState%2A> di ciascuna riga di dati della tabella.  
  
 Quando si salvano i dati nelle tabelle correlate, Visual Studio fornisce un nuovo componente TableAdapterManager che consente di eseguire i salvataggi nell'ordine corretto in base ai vincoli di chiave esterna definiti nel database.  Per ulteriori informazioni, vedere [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md).  
  
> [!NOTE]
>  Poiché il tentativo di aggiornare un'origine dati con il contenuto di un dataset può provocare degli errori, è necessario posizionare il codice che chiama il metodo `Update` dell'adattatore all'interno di un blocco `try`\/`catch`.  
  
 La procedura corretta per aggiornare un'origine dati può variare a seconda delle esigenze aziendali, ma l'applicazione dovrà comprendere i seguenti passaggi:  
  
1.  Eseguire il codice che consente di inviare gli aggiornamenti al database all'interno di un blocco `try`\/`catch`.  
  
2.  Se si intercetta un'eccezione, individuare la riga di dati che ha provocato l'errore.  Per ulteriori informazioni, vedere [Procedura: individuare righe con errori](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).  
  
3.  Risolvere il problema nella riga di dati, se possibile a livello di codice oppure presentando la riga non valida all'utente per la modifica, quindi tentare nuovamente l'aggiornamento \(proprietà <xref:System.Data.DataRow.HasErrors%2A>, metodo <xref:System.Data.DataTable.GetErrors%2A>\).  
  
## Salvataggio dei dati in un database  
 Chiamare il metodo `Update` di un oggetto TableAdapter o di un adattatore dati passando il nome della tabella di dati contenente i valori da scrivere nel database.  Per ulteriori informazioni sul salvataggio dei dati da una singola tabella di dati in un database, vedere [Procedura dettagliata: salvataggio di dati in un database \(a tabella singola\)](../Topic/Walkthrough:%20Saving%20Data%20to%20a%20Database%20\(Single%20Table\).md).  
  
#### Per aggiornare un database con un dataset mediante un TableAdapter  
  
-   Racchiudere il metodo `TableAdapter.Update` all'interno di un blocco `try`\/`catch`.  Nel seguente esempio viene illustrato un tentativo di aggiornamento con il contenuto della tabella `Customers` nel dataset `NorthwindDataSet`.  
  
     [!code-cs[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_1.vb)]  
  
#### Per aggiornare un database con un dataset mediante un adattatore dati  
  
-   Racchiudere il metodo `DataAdapter.Update` all'interno di un blocco `try`\/`catch`.  Nel seguente esempio viene illustrata la procedura per tentare l'aggiornamento di un'origine dati con il contenuto di `Table1` in `DataSet1`.  
  
     [!code-vb[VbRaddataSaving#26](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#26](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_2.cs)]  
  
## Aggiornamento di due tabelle correlate in un dataset  
 Quando si aggiornano le tabelle correlate in un dataset, è importante effettuare l'aggiornamento nella sequenza corretta, in modo da ridurre la possibilità di violare i vincoli di integrità referenziale.  L'ordine di esecuzione dei comandi seguirà anche gli indici dell'oggetto <xref:System.Data.DataRowCollection> nel dataset.  Per impedire che vengano generati errori di integrità dei dati, è preferibile aggiornare il database rispettando questa sequenza:  
  
1.  Tabella figlio: eliminare i record.  
  
2.  Tabella padre: inserire, aggiornare ed eliminare i record.  
  
3.  Tabella figlio: inserire e aggiornare i record.  
  
 Per informazioni dettagliate sul salvataggio dei dati di più tabelle, vedere [Procedura dettagliata: salvataggio di dati in un database \(a più tabelle\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
 Se è in corso l'aggiornamento di due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione.  Una transazione è un processo che garantisce il corretto inserimento di tutte le modifiche correlate in un database prima del relativo commit.  Per ulteriori informazioni, vedere [Transazioni e concorrenza](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Per aggiornare due tabelle correlate mediante un TableAdapter  
  
1.  Creare tre oggetti <xref:System.Data.DataTable> temporanei in cui collocare i diversi record.  
  
2.  Chiamare il metodo `Update` per ciascun sottoinsieme di righe dall'interno di un blocco `try`\/`catch`.  Se si verificano errori di aggiornamento, l'operazione da eseguire consiste nell'interrompere il processo e risolverli.  
  
3.  Eseguire il commit delle modifiche dal dataset al database.  
  
4.  Eliminare le tabelle di dati temporanee per liberare le risorse.  
  
     [!code-vb[VbRaddataSaving#27](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#27](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_3.cs)]  
  
#### Per aggiornare due tabelle correlate mediante un adattatore dati  
  
-   Chiamare il metodo `Update` di ciascun adattatore dati.  
  
     Nell'esempio seguente viene illustrata la procedura per aggiornare un'origine dati con un dataset che contiene tabelle correlate.  Per rispettare la sequenza sopra riportata, verranno creati tre oggetti <xref:System.Data.DataTable> temporanei per contenere i diversi record.  Verrà quindi chiamato il metodo `Update` per ciascun sottoinsieme di righe dall'interno di un blocco `try`\/`catch`.  Se si verificano errori di aggiornamento, l'operazione da eseguire consiste nell'interrompere il processo e risolverli.  Verranno quindi applicate le modifiche.  Eliminare infine gli oggetti tabelle di dati temporanei per liberare le risorse.  
  
     [!code-vb[VbRaddataSaving#28](../data-tools/codesnippet/VisualBasic/how-to-save-dataset-changes-to-a-database_4.vb)]
     [!code-cs[VbRaddataSaving#28](../data-tools/codesnippet/CSharp/how-to-save-dataset-changes-to-a-database_4.cs)]  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)