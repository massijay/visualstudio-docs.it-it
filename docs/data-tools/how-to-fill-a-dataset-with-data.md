---
title: "Procedura: riempire un dataset | Microsoft Docs"
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
  - "dati [Visual Basic], caricamento in dataset"
  - "dataset [Visual Basic], riempimento"
  - "DataTable (oggetti), caricamento"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: riempire un dataset
La compilazione di un dataset con dei dati consiste in realtà nel caricamento dei dati nei singoli oggetti <xref:System.Data.DataTable> che costituiscono il dataset.  Le tabelle di dati vengono compilate mediante l'esecuzione di query TableAdapter o di comandi dell'adattatore dati, ad esempio <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
 La scelta di utilizzare TableAdapter o adattatori dati dipende dalla modalità di creazione del dataset.  Se sono stati utilizzati gli strumenti di progettazione disponibili in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], come la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png), il dataset conterrà TableAdapter.  Per ulteriori informazioni sui TableAdapter, vedere [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md).  Se il database è stato creato a livello di codice, in genere è necessario creare adattatori dati per caricare i dati nelle tabelle dati.  
  
> [!NOTE]
>  Quando si trascinano elementi dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) in un form, il codice che consente di riempire la tabella dati con i dati viene automaticamente aggiunto al gestore eventi `Form_Load`.  Aprire il form nell'editor di codice per visualizzare la sintassi esatta per il riempimento di tabelle specifiche.  Se non si desidera riempire la tabella al momento del caricamento del form, è possibile spostare il codice in un altro metodo o rimuoverlo completamente.  
  
## Compilazione di un dataset mediante un oggetto TableAdapter  
 È possibile chiamare una query sul TableAdapter per caricare i dati nelle tabelle di un dataset.  Passare l'oggetto <xref:System.Data.DataTable> da riempire alla query TableAdapter.  Se la query accetta parametri, passare anche questi al metodo.  Se il dataset contiene più tabelle, ognuna di esse dovrà disporre di uno specifico TableAdapter e dovrà essere compilata separatamente.  
  
> [!NOTE]
>  Per impostazione predefinita, ogni volta che si esegue una query TableAdapter, i dati della tabella vengono cancellati prima del caricamento dei risultati della query nella tabella stessa.  È possibile conservare i dati esistenti nella tabella e aggiungere i risultati impostando la proprietà `ClearBeforeFill` del TableAdapter su `false`.  
  
#### Per riempire un dataset utilizzando un TableAdapter  
  
1.  Aprire il form o il componente nell'**editor di codice**.  
  
2.  Aggiungere codice in un punto dell'applicazione in cui è necessario caricare una tabella contenente dati.  Se la query non accetta parametri, passare l'oggetto <xref:System.Data.DataTable> da riempire.  Il codice dovrebbe risultare simile al seguente:  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  Se la query accetta parametri, passare l'oggetto <xref:System.Data.DataTable> da riempire e i parametri previsti dalla query.  A seconda dei parametri effettivi della query, il codice dovrebbe risultare simile a quello dei seguenti esempi:  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## Compilazione di un dataset mediante un oggetto DataAdapter  
 Chiamare il metodo `Fill` dell'adattatore dati.  L'adattatore eseguirà l'istruzione SQL o la stored procedure alla quale fa riferimento la relativa proprietà `SelectCommand` e inserirà i risultati in una tabella del dataset.  Se il dataset contiene più tabelle, ogni tabella dovrà disporre di uno specifico adattatore dati e dovrà essere riempita separatamente.  
  
#### Per riempire un dataset utilizzando un DataAdapter  
  
-   Chiamare il metodo <xref:System.Data.Common.DataAdapter.Fill%2A> dell'oggetto <xref:System.Data.Common.DataAdapter>, passando l'oggetto <xref:System.Data.DataSet> o <xref:System.Data.DataTable> nel quale caricare i dati.  Di seguito è riportato un esempio:  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     Generalmente si procede fornendo il nome dell'oggetto <xref:System.Data.DataTable> nel quale caricare i dati.  Se si passa il nome di un oggetto <xref:System.Data.DataSet> anziché quello di una specifica tabella di dati, un oggetto <xref:System.Data.DataTable> denominato `Table1` verrà aggiunto al dataset e caricato con i risultati del database \(anziché caricare i dati in un oggetto <xref:System.Data.DataTable> esistente nel dataset\).  Per ulteriori informazioni, vedere [Compilazione di un DataSet da un oggetto DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
## Vedere anche  
 [Inserimento di dati nei dataset](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)