---
title: "Procedura: disattivare i vincoli durante il riempimento di un dataset | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataRow.BeginEdit"
  - "DataRow.EndEdit"
  - "DataRow.CancelEdit"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "vincoli [Visual Basic], dataset"
  - "vincoli [Visual Basic], sospensione durante l'aggiornamento di dataset"
  - "dataset [Visual Basic], vincoli"
  - "aggiornamento di dataset, vincoli"
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: disattivare i vincoli durante il riempimento di un dataset
Se un dataset contiene dei vincoli, quale un vincolo di chiave esterna, è possibile fare in modo che vengano generate delle eccezioni a seconda dell'ordine di esecuzione delle operazioni sul dataset.  Il caricamento di record figlio antecedente al caricamento dei relativi record padre, ad esempio, può determinare una violazione del vincolo e generare un'eccezione.  Non appena viene caricato un record figlio, il vincolo verifica se è presente anche il relativo record figlio e segnala un errore.  Se non fossero presenti dei meccanismi per consentire una sospensione temporanea dei vincoli, verrebbe generato un errore ogni volta si tenta di caricare un record nella tabella figlio.  Un ulteriore sistema per sospendere tutti i vincoli di un dataset prevede l'utilizzo delle proprietà <xref:System.Data.DataRow.BeginEdit%2A> e <xref:System.Data.DataRow.EndEdit%2A>.  
  
> [!NOTE]
>  Gli eventi di convalida, ad esempio <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging> e così via\) non verranno generati se i vincoli sono disattivati.  
  
### Per sospendere i vincoli di aggiornamento a livello di codice  
  
-   Nell'esempio seguente viene illustrato come disattivare temporaneamente il controllo dei vincoli in un dataset:  
  
     [!CODE [VbRaddataEditing#10](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#10)]  
  
### Per sospendere i vincoli di aggiornamento mediante la finestra Progettazione DataSet  
  
1.  Aprire il dataset in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Impostare la proprietà <xref:System.Data.DataSet.EnforceConstraints%2A> su `false` nella finestra **Proprietà**.  
  
## Vedere anche  
 [Salvataggio dei dati nei dataset](../data-tools/save-data-back-to-the-database.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)