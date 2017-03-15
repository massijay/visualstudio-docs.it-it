---
title: "Procedura: creare query TableAdapter | Microsoft Docs"
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
  - "dati [Visual Studio], TableAdapter (query)"
  - "query [Visual Studio], creazione"
  - "query [Visual Studio], TableAdapters"
  - "TableAdapters, creazione di query"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: creare query TableAdapter
Le query TableAdapter sono istruzioni SQL oppure stored procedure che possono essere eseguite dall'applicazione in uso su un database.  
  
 È possibile aggiungere a un TableAdapter tante query quante sono necessarie per l'applicazione.  Le query TableAdapter vengono visualizzate su un TableAdapter come metodi.  Quando viene creata una query denominata `FillByCity` che utilizza un parametro che rappresenta il valore relativo alla città, la query viene aggiunta all'oggetto TableAdapter  come metodo tipizzato che accetta il tipo corretto di parametro come argomento, in questo caso una stringa che rappresenta il valore per la città.  La query TableAdapter viene chiamata come qualsiasi metodo su qualunque oggetto.  Ad esempio, il codice riportato di seguito consente di eseguire la query `FillByCity` e di riempire la tabella `Customers` con tutti i clienti che per città hanno il valore `Seattle`:  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 Le query TableAdapter consentono di riempire una tabella di dati \(query `Fill` e `FillBy`\) oppure di restituire nuove tabelle di dati compilate con i dati restituiti dalla query \(query `GetData` e `GetDataBy`\).  
  
 È possibile aggiungere query ai TableAdapter mediante l'esecuzione della [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md).  Fare clic con il pulsante destro del mouse su un oggetto TableAdapter qualsiasi e scegliere **Aggiungi query**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Creazione di una query nella finestra Progettazione DataSet  
  
#### Per aggiungere una query a un TableAdapter nella finestra Progettazione DataSet  
  
1.  Aprire un dataset in **Progettazione DataSet**.  Per ulteriori informazioni, vedere [Procedura: aprire un dataset in Progettazione DataSet](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Fare clic con il pulsante destro del mouse sul TableAdapter desiderato e selezionare **Aggiungi query**.  
  
     In alternativa  
  
3.  Trascinare un oggetto **Query** dalla scheda **DataSet** della **Casella degli strumenti** su una tabella nella finestra di progettazione.  
  
     Viene aperta la **Configurazione guidata query TableAdapter**.  
  
4.  Completare la procedura guidata. La query verrà aggiunta al TableAdapter.  
  
## Creazione di una query direttamente in un form dell'applicazione Windows in uso  
 Se il form contiene un'istanza di un oggetto TableAdapter, è possibile aggiungere una query mediante la [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md), che consente di aggiungere al form un controllo <xref:System.Windows.Forms.ToolStrip> che accetta qualsiasi parametro di input richiesto dalla query, oltre a un pulsante per eseguire la query.  
  
#### Per aggiungere una query a un TableAdapter mediante la finestra di dialogo Generatore di criteri per la ricerca  
  
1.  Selezionare un oggetto TableAdapter nella barra dei componenti.  
  
2.  Fare clic sullo smart tag del TableAdapter, quindi scegliere **Aggiungi query**.  
  
3.  Compilare la finestra di dialogo e la query verrà aggiunta al TableAdapter.  Per ulteriori informazioni, vedere [Finestra di dialogo Generatore di criteri per la ricerca](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Procedura: esplorare i dati con il controllo BindingNavigator Windows Form](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Procedura dettagliata: creazione di un oggetto TableAdapter con più query](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)