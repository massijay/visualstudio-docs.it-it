---
title: "Modifica di dati nei dataset | Microsoft Docs"
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
helpviewer_keywords: 
  - "dati [Visual Studio], modifica in dataset"
  - "dataset [Visual Basic], modifica di dati"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Modifica di dati nei dataset
La modifica dei dati in un oggetto <xref:System.Data.DataSet> consiste nel processo di modifica dei dati effettivi contenuti nei singoli oggetti <xref:System.Data.DataTable> che formano un dataset.  Le modifiche che è possibile apportare nelle tabelle dati sono simili alle modifiche apportate a una tabella di un qualsiasi database includono l'inserimento, l'aggiornamento e l'eliminazione dei record all'interno della tabella.  
  
 Oltre alla modifica dei dati effettivi, è possibile anche eseguire query a un oggetto <xref:System.Data.DataTable> per restituire righe di dati specifiche, ad esempio, singole righe, versioni specifiche di righe \(originali e proposte\), soltanto le righe modificate e le righe in cui sono presenti degli errori.  
  
## Attività comuni delle tabelle dati  
 Nella tabella riportata di seguito sono forniti i collegamenti alle attività comuni associate alla modifica e all'esecuzione di query di dati in un dataset:  
  
|Task|Descrizione|  
|----------|-----------------|  
|Inserimento di nuovi record in una tabella dati.|Creare un nuovo oggetto <xref:System.Data.DataRow> e aggiungerlo alla raccolta di righe della tabella.  Per ulteriori informazioni, vedere [Procedura: aggiungere righe a una DataTable](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md).|  
|Aggiornamento di record esistenti in una tabella dati.|Assegnare un valore direttamente alla colonna specifica di una riga di dati.  Per ulteriori informazioni, vedere [Procedura: modificare le righe in un oggetto DataTable](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md).|  
|Eliminazione di record esistenti da una tabella dati.|Chiamare il metodo <xref:System.Data.DataRow.Delete%2A> della riga di dati da rimuovere dalla tabella.  Per ulteriori informazioni, vedere [Procedura: eliminare righe in un oggetto DataTable](../Topic/How%20to:%20Delete%20Rows%20in%20a%20DataTable.md).|  
|Individuazione dei record modificati in una tabella dati.|Chiamare il metodo <xref:System.Data.DataTable.GetChanges%2A> di una tabella dati.  Per ulteriori informazioni, vedere [Procedura: recuperare le righe modificate](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).|  
|Accesso alle diverse versioni di una riga in una tabella dati.|Accedere alle colonne singole di una riga di dati passando l'oggetto <xref:System.Data.DataRowVersion> da visualizzare.  Per ulteriori informazioni, vedere [Procedura: ottenere versioni specifiche di un DataRow](../data-tools/how-to-get-specific-versions-of-a-datarow.md).|  
|Individuazione delle righe contenenti errori in una tabella dati.|Esaminare la proprietà <xref:System.Data.DataTable.HasErrors%2A> di una tabella dati.  Per ulteriori informazioni, vedere [Procedura: individuare righe con errori](../Topic/How%20to:%20Locate%20Rows%20that%20Have%20Errors.md).|  
  
## Vedere anche  
 [DataTable](../Topic/DataTables.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [DataTable](../Topic/DataTables.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)