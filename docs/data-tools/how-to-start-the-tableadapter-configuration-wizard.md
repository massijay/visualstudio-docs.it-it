---
title: "Procedura: avviare la Configurazione guidata TableAdapter | Microsoft Docs"
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
  - "TableAdapter (configurazione guidata)"
  - "TableAdapters, configurazione guidata"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: avviare la Configurazione guidata TableAdapter
La **Configurazione guidata TableAdapter** crea e modifica TableAdapter in set di dati fortemente tipizzati.  La procedura guidata crea TableAdapter in base alle istruzioni SQL inserite nella procedura stessa o in base a stored procedure esistenti nel database.  Può anche creare nuove stored procedure nel database in base alle istruzioni SQL inserite nella procedura stessa.  
  
### Per avviare la Configurazione guidata TableAdapter per creare un nuovo TableAdapter  
  
1.  Aprire il set di dati in **Progettazione DataSet**.  Per altre informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
    > [!NOTE]
    >  Se nel progetto non sono presenti set di dati, vedere [Procedura: creare un dataset tipizzato](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Se si sta creando un nuovo TableAdapter, trascinare un oggetto **TableAdapter** dalla scheda **DataSet** della **Casella degli strumenti** in **Progettazione DataSet**.  
  
3.  Nella pagina **Seleziona connessione dati** selezionare una connessione dati nell'elenco delle connessioni attualmente disponibili oppure selezionare **Nuova connessione** per creare una nuova connessione.  
  
### Per avviare la Configurazione guidata TableAdapter per modificare un TableAdapter esistente  
  
1.  Aprire il set di dati in **Progettazione DataSet**.  Per altre informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Fare clic con il pulsante destro del mouse su TableAdapter in **Progettazione DataSet**, quindi scegliere **Configura**.  Sarà visualizzata la pagina **Genera le istruzioni SQL** o la pagina **Associa comandi alle stored procedure esistenti** della procedura guidata, in base alla modalità di configurazione originale di TableAdapter.  
  
3.  Completare la procedura guidata.  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Procedura: ordinare e filtrare i dati ADO.NET con il componente BindingSource Windows Form](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Procedura: creare una tabella di ricerca con il componente BindingSource di Windows Form](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)