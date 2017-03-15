---
title: "Procedura: aggiungere il codice nei dataset di applicazioni a pi&#249; livelli | Microsoft Docs"
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
  - "applicazioni a più livelli, estensione di dataset"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: aggiungere il codice nei dataset di applicazioni a pi&#249; livelli
È possibile estendere la funzionalità di un dataset creando un file di classe parziale per il dataset e aggiungendovi il codice, anziché aggiungere il codice al file *NomeDataset*.Dataset.Designer.  Mediante le classi parziali è possibile suddividere il codice di una classe specifica tra più file fisici.   Per ulteriori informazioni, vedere [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [Classi e metodi parziali](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 Il codice che definisce un dataset viene generato ogni volta che vengono apportate modifiche alla definizione del dataset in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che modifica la configurazione di un dataset.  Per evitare l'eliminazione del codice durante la rigenerazione di un dataset, è possibile aggiungere il codice al file di classe parziale del dataset.  
  
 Per impostazione predefinita, dopo avere separato il codice del dataset e il codice del `TableAdapter`, il risultato sarà un file di classe discreto in ogni progetto.  Nel progetto originale sarà presente un file denominato *NomeDataset*.Designer.vb o *NomeDataset*.Designer.cs contenente il codice `TableAdapter`.  Nel progetto definito nella proprietà **Progetto DataSet** sarà presente un file denominato *NomeDataset*.DataSet.Designer.vb o *NomeDataset*.DataSet.Designer.cs contenente il codice del dataset.  
  
> [!NOTE]
>  Quando si separano i dataset e i `TableAdapter` impostando la proprietà **DataSet Project**, le classi del dataset parziale presenti nel progetto non verranno spostate automaticamente.  Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) consente inoltre di generare i gestori eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> quando viene aggiunto il codice di convalida.  Per ulteriori informazioni, vedere [Procedura: aggiungere la convalida a un dataset a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### Per aggiungere il codice nei dataset di applicazioni a più livelli  
  
1.  Individuare il progetto contenente il file xsd \([Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Fare doppio clic sul file **xsd** per aprire [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Fare clic con il pulsante destro del mouse sulla tabella dati in cui si desidera aggiungere il codice e scegliere **Visualizza codice**. Il nome della tabella viene visualizzato nella barra del titolo.  
  
     Viene creata una classe parziale e visualizzata nell'editor del codice.  
  
4.  Aggiungere il codice nella dichiarazione di classe parziale.  
  
     Nell'esempio seguente viene illustrato dove aggiungere il codice in CustomersDataTable di NorthwindDataSet:  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## Vedere anche  
 [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Procedura: aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md)   
 [Creazione di applicazioni dati](../data-tools/creating-data-applications.md)   
 [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)