---
title: "Procedura: creare tabelle di dati | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], creazione di tabelle di dati"
  - "Progettazione DataSet, creazione di tabelle di dati"
  - "tabelle [Visual Studio], creazione"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: creare tabelle di dati
È possibile memorizzare i dati negli oggetti <xref:System.Data.DataTable>. I dataset sono costituiti da oggetti <xref:System.Data.DataTable>. Di norma le nuove tabelle di dati vengono create con oggetti TableAdapter mediante la [TableAdapter \(configurazione guidata\)](../Topic/TableAdapter%20Configuration%20Wizard.md) oppure mediante il trascinamento di oggetti di database da **Esplora server** nella finestra **Progettazione DataSet**.  
  
 Le tabelle di dati vengono create come sottoprodotto quando si creano nuovi TableAdapter mediante la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png), ma possono essere create anche indipendentemente.  Per creare una tabella dati autonoma, trascinare un oggetto <xref:System.Data.DataTable> dalla scheda **DataSet** della **Casella degli strumenti** in **Progettazione DataSet**.  
  
> [!NOTE]
>  Per creare tabelle di dati a livello di codice, vedere [Creazione di una DataTable](../Topic/Creating%20a%20DataTable.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Creazione di una DataTable con TableAdapter  
 Le tabelle dati con TableAdapter includono metodi che consentono di inserire dati nella tabella e di scrivere le modifiche nel database.  La creazione dei TableAdapter avviene mediante l'esecuzione della **Configurazione guidata TableAdapter** oppure mediante il trascinamento di oggetti di database da **Esplora server** in **Progettazione DataSet**.  
  
#### Per creare una nuova tabella dati con TableAdapter  
  
1.  Aprire il dataset in **Progettazione DataSet**.  Per informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Trascinare un **TableAdapter** dalla scheda **DataSet** della **Casella degli strumenti** in **Progettazione DataSet**.  
  
     Verrà avviata la **Configurazione guidata TableAdapter**.  
  
3.  Completare la procedura guidata.  Per ulteriori informazioni, vedere [TableAdapter \(configurazione guidata\)](../Topic/TableAdapter%20Configuration%20Wizard.md).  
  
#### Per creare una nuova tabella di dati con un oggetto TableAdapter da Esplora server  
  
1.  Aprire il dataset in **Progettazione DataSet**.  
  
2.  Trascinare un oggetto di database, ad esempio una tabella, da **Esplora server** in **Progettazione DataSet**.  
  
## Creazione di una DataTable autonoma  
 Per poter riempire con dati le tabelle autonome, è necessario che la relativa logica `Fill` sia implementata.  Per informazioni su come inserire dati nelle tabelle di dati autonome, vedere [Compilazione di un DataSet da un oggetto DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
#### Per creare una nuova tabella dati autonoma  
  
1.  Aprire il dataset in **Progettazione DataSet**.  
  
2.  Trascinare un oggetto <xref:System.Data.DataTable> dalla scheda **DataSet** della **Casella degli strumenti** nella finestra **Progettazione DataSet**.  
  
3.  Aggiungere colonne per definire la tabella dati.  Per ulteriori informazioni, vedere [Procedura: aggiungere colonne a un oggetto DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md).  
  
## Vedere anche  
 <xref:System.Data.DataTable>   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)