---
title: "Creazione e modifica di dataset tipizzati | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], Progettazione DataSet"
  - "Progettazione DataSet"
  - "dataset [Visual Basic], finestra di progettazione di Visual"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Creazione e modifica di dataset tipizzati
La finestra **Progettazione DataSet** è un insieme di strumenti visivi che consentono di creare e modificare dataset tipizzati ed i singoli elementi che costituiscono i dataset.  
  
 **Progettazione Dataset** fornisce rappresentazioni visive degli oggetti contenuti in dataset tipizzati  e consente di creare e modificare oggetti [TableAdapter](../data-tools/tableadapter-overview.md), [query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>, <xref:System.Data.DataColumn>, e <xref:System.Data.DataRelation> con il **Dataset Designer**.  
  
 Per aprire la finestra **Progettazione DataSet**, fare doppio clic su un database in **Esplora soluzioni** oppure fare clic con il pulsante destro del mouse su un dataset nella finestra **Origini dati** e scegliere **Modifica il Dataset con la finestra di progettazione**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  Aggiungendo un nuovo elemento <xref:System.Data.DataSet> mediante la finestra di dialogo **Aggiungi nuovo elemento** verrà aperta una finestra **Progettazione DataSet** contenente un dataset vuoto pronto per essere modificato.  
  
> [!NOTE]
>  La finestra **Progettazione DataSet** può essere utilizzata per estendere la funzionalità di un dataset.  Fare doppio clic nell'area di progettazione oppure fare clic con il pulsante destro del mouse e scegliere **Visualizza codice** per creare un file di classe parziale da utilizzare per aggiungere al dataset del codice che non verrà modificato o eliminato dalla funzione di progettazione.  Per informazioni sull'estensione della funzionalità di un oggetto TableAdapter, vedere [Procedura: estendere la funzionalità di un TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 Nella tabella che segue sono elencate le attività più comuni che è possibile eseguire con **Progettazione DataSet**.  
  
|Per|Vedere|  
|---------|------------|  
|Creare un TableAdapter|[Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|Modificare un TableAdapter|[Procedura: modificare oggetti TableAdapter](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|Creare una query di TableAdapter|[Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Modificare una query di TableAdapter|[Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Creare un oggetto <xref:System.Data.DataTable>|[Procedura: creare tabelle di dati](../data-tools/how-to-create-data-tables.md)|  
|Modificare una <xref:System.Data.DataTable>|[Progettazione di DataTable](../data-tools/designing-datatables.md)|  
|Creare un oggetto <xref:System.Data.DataColumn>|[Procedura: aggiungere colonne a un oggetto DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|Creare una relazione fra due <xref:System.Data.DataTable>|[Procedura: creare DataRelation mediante Progettazione DataSet](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|Estendere la funzionalità del dataset|[Procedura: estendere la funzionalità di un dataset](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|Aggiungere codice di convalida all'evento <xref:System.Data.DataTable.ColumnChanging> di una tabella dati|[Procedura: convalidare i dati durante la modifica delle colonne](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|Aggiungere codice di convalida all'evento <xref:System.Data.DataTable.RowChanging> di una tabella dati|[Procedura: convalidare i dati durante la modifica delle righe](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## Creazione di oggetti nell'area di progettazione  
 È possibile creare un dataset aggiungendo e modificando i singoli oggetti che costituiscono un dataset.  Nella tabella seguente viene fornita una spiegazione dei vari oggetti disponibili nella scheda **DataSet** della **Casella degli strumenti** che è possibile trascinare nell'area di progettazione:  
  
|Object|Descrizione|  
|------------|-----------------|  
|TableAdapter|Contiene una raccolta di comandi di dati e una connessione dati utilizzati per comunicare con il database sottostante e compilare una tabella di dati.  Per ulteriori informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md) e [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Query|Le query di TableAdapter sono metodi fortemente tipizzati che eseguono stored procedure e istruzioni SQL.  L'esecuzione di una query TableAdapter popola di dati le tabelle dati o esegue altre attività di database.  Per ulteriori informazioni, vedere [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  Se una query viene trascinata in una tabella, essa viene aggiunta alla tabella, mentre se si trascina una query in un'area vuota della finestra **Progettazione DataSet** viene creata una query globale.  Per ulteriori informazioni, vedere [Procedura: aggiungere query globali a un dataset](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Rappresenta una raccolta in memoria delle righe restituite da un database.|  
|Relation \(<xref:System.Data.DataRelation>\)|Rappresenta una relazione padre\/figlio tra due <xref:System.Data.DataTable>.  Per ulteriori informazioni, vedere [Introduzione agli oggetti DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md) e [Procedura dettagliata: creazione di una relazione tra tabelle dati](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md).|  
  
> [!NOTE]
>  **Progettazione Dataset** si connette ad un database sottostante solo quando un dataset viene creato; la finestra di progettazione non rileva automaticamente le successive modifiche al database.  Per aggiornare un file .xsd esistente, eseguire nuovamente **Configurazione guidata**.  Se le relazioni della tabella sono state modificate, rimuovere e aggiungere nuovamente le tabelle relative al file .xsd.  
  
## Da LINQ a DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] abilita [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) su dati in un oggetto <xref:System.Data.DataSet>.  Per ulteriori informazioni, vedere [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Vedere anche  
 [Procedura dettagliata: creazione di un dataset con Progettazione DataSet](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Procedura dettagliata: creazione di un oggetto TableAdapter con più query](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Procedura dettagliata: creazione di una DataTable in Progettazione DataSet](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Procedura dettagliata: creazione di una relazione tra tabelle dati](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)