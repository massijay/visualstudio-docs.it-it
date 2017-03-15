---
title: "Procedura: ottenere versioni specifiche di un DataRow | Microsoft Docs"
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
  - "DataRow (oggetto)"
  - "stati righe"
  - "aggiornamento di dataset, stati righe"
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: ottenere versioni specifiche di un DataRow
Quando si apportano modifiche alle righe di dati, il dataset mantiene sia la versione originale \(<xref:System.Data.DataRowVersion>\) che quella nuova \(<xref:System.Data.DataRowVersion>\) della riga.  Prima di chiamare il metodo `AcceptChanges`, ad esempio, sarà possibile accedere alle diverse versioni di un record, definite nell'enumerazione <xref:System.Data.DataRowVersion>, ed effettuare le modifiche necessarie.  
  
> [!NOTE]
>  La presenza di versioni diverse di una riga si verifica solo in seguito alla sua modifica e prima della chiamata del metodo `AcceptChanges`.  Una volta chiamato il metodo `AcceptChanges`, la versione corrente e la versione originale coincideranno.  
  
 Se si passa il valore <xref:System.Data.DataRowVersion> insieme all'indice di colonna, o al nome di colonna come stringa, viene restituito il valore della versione specifica della riga presente in quella colonna.  La colonna modificata viene identificata durante gli eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged>. A questo punto è possibile analizzare le diverse versioni della riga per eseguire la convalida.  Tuttavia, se i vincoli sono stati sospesi temporaneamente, questi eventi non verranno generati e sarà necessario identificare a livello di codice le colonne modificate.  A tale scopo, scorrere la raccolta <xref:System.Data.DataTable.Columns%2A> e confrontare i diversi valori <xref:System.Data.DataRowVersion>.  
  
## Accesso alla versione originale di una DataRow  
  
#### Per ottenere la versione originale di un record  
  
-   Accedere al valore di una colonna passando il valore <xref:System.Data.DataRowVersion> della riga che deve venire restituita.  
  
     Nell'esempio che segue viene illustrato l'utilizzo del valore <xref:System.Data.DataRowVersion> per ottenere il valore originale di un campo `CompanyName` in una <xref:System.Data.DataRow>.  
  
     [!CODE [VbRaddataEditing#21](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#21)]  
  
## Accesso alla versione corrente di una DataRow  
  
#### Per ottenere la versione corrente di un record  
  
-   Accedere al valore di una colonna e aggiungere all'indice un parametro che indichi la versione della una riga che si desidera restituire.  
  
     Nell'esempio che segue viene illustrato l'utilizzo del valore <xref:System.Data.DataRowVersion> per ottenere il valore corrente di un campo `CompanyName` in una <xref:System.Data.DataRow>.  
  
     [!CODE [VbRaddataEditing#22](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#22)]  
  
## Vedere anche  
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)