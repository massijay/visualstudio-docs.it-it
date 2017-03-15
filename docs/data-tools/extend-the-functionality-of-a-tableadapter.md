---
title: "Procedura: estendere la funzionalit&#224; di un TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "dati [Visual Studio], estensione di TableAdapter"
  - "dati [Visual Studio], TableAdapters"
  - "TableAdapters, aggiunta di funzionalità"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: estendere la funzionalit&#224; di un TableAdapter
È possibile estendere la funzionalità di un TableAdapter aggiungendo il codice al file di classe parziale del TableAdapter.  
  
 Il codice che definisce un TableAdapter viene rigenerato quando si effettuano modifiche al TableAdapter \(nella finestra di progettazione **Progettazione DataSet**\) oppure quando si effettuano modifiche alla configurazione di un TableAdapter in fase di esecuzione di una procedura guidata.  Per evitare l'eliminazione del codice durante la rigenerazione di un TableAdapter, aggiungere codice al file di classe parziale del TableAdapter.  
  
 Mediante le classi parziali è possibile suddividere il codice di una classe specifica tra più file fisici.  Per ulteriori informazioni, vedere [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [parziale \(Tipo\)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
## Individuazione dei TableAdapter nel codice.  
 Sebbene i TableAdapter vengano progettati con **Progettazione DataSet**, le classi TableAdapter generate non vengono create come classi annidate di <xref:System.Data.DataSet> I TableAdapter sono posizionati in uno spazio dei nomi in base al nome del dataset associato al TableAdapter.  Ad esempio, se nell'applicazione in uso è contenuto un dataset denominato `HRDataSet`, i TableAdapters sono posizionati nello spazio dei nomi `HRDataSetTableAdapters`.  Nella convenzione di denominazione si segue il modello riportato di seguito: *NomeDataset* \+ `TableAdapters`.  
  
 Nell'esempio riportato di seguito si presuppone un TableAdapter denominato `CustomersTableAdapter` in un progetto con un dataset `NorthwindDataSet`.  
  
#### Per creare una classe parziale per un TableAdapter  
  
1.  Aggiungere una nuova classe al progetto scegliendo **Aggiungi classe** dal menu **Progetto**.  
  
2.  Denominare la classe `CustomersTableAdapterExtended`.  
  
3.  Scegliere **Aggiungi**.  
  
4.  Sostituire il codice con lo spazio dei nomi e il nome della classe parziale appropriati al progetto in uso.  Di seguito è riportato un esempio:  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedura: estendere la funzionalità di un dataset](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)