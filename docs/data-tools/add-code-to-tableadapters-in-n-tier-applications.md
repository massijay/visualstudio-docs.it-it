---
title: "Procedura: aggiungere il codice nei TableAdapter di applicazioni a pi&#249; livelli | Microsoft Docs"
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
  - "applicazioni a più livelli, estensione di TableAdapter"
  - "TableAdapters, applicazioni a più livelli"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: aggiungere il codice nei TableAdapter di applicazioni a pi&#249; livelli
È possibile estendere la funzionalità di un `TableAdapter` creando un file di classe parziale per il `TableAdapter` e aggiungendovi il codice, anziché aggiungere il codice al file *NomeDataset*.DataSet.Designer.  Mediante le classi parziali è possibile suddividere il codice di una classe specifica tra più file fisici.   Per ulteriori informazioni, vedere [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [parziale \(Tipo\)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
 Il codice che definisce un `TableAdapter` viene generato ogni volta che vengono apportate modifiche al `TableAdapter` in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che modifica la configurazione del `TableAdapter`.  Per evitare l'eliminazione del codice durante la rigenerazione di un `TableAdapter`, è possibile aggiungere il codice al file di classe parziale del `TableAdapter`.  
  
 Per impostazione predefinita, dopo avere separato il codice del dataset e il codice del `TableAdapter`, il risultato sarà un file di classe discreto in ogni progetto.  Nel progetto originale sarà presente un file denominato *NomeDataset*.Designer.vb o *NomeDataset*.Designer.cs contenente il codice `TableAdapter`.  Nel progetto definito nella proprietà **Progetto DataSet** sarà presente un file denominato *NomeDataset*.DataSet.Designer.vb o *NomeDataset*.DataSet.Designer.cs contenente il codice del dataset.  
  
> [!NOTE]
>  Quando si separano i dataset e i `TableAdapter` impostando la proprietà **DataSet Project**, le classi del dataset parziale presenti nel progetto non verranno spostate automaticamente.  Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) consente inoltre di generare i gestori eventi <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> quando viene aggiunto il codice di convalida.  Per ulteriori informazioni, vedere [Procedura: aggiungere la convalida a un dataset a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per aggiungere il codice utente in un TableAdapter di applicazioni a più livelli  
  
1.  Individuare il progetto contenente il file xsd \([Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Fare doppio clic sul file **xsd** per aprire [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Fare clic con il pulsante destro del mouse sul `TableAdapter` in cui si desidera aggiungere il codice e scegliere **Visualizza codice**.  
  
     Viene creata una classe parziale e visualizzata nell'editor del codice.  
  
4.  Aggiungere il codice nella dichiarazione di classe parziale.  
  
5.  Nell'esempio seguente viene illustrato dove aggiungere il codice nel `CustomersTableAdapter` di `NorthwindDataSet`:  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## Vedere anche  
 [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Procedura: aggiungere il codice nei dataset di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Cenni preliminari sull'aggiornamento gerarchico](../Topic/Hierarchical%20Update%20Overview.md)   
 [Creazione di applicazioni dati](../data-tools/creating-data-applications.md)