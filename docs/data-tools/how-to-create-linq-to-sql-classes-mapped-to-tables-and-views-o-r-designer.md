---
title: "Procedura: creare classi LINQ to SQL con mapping a tabelle e visualizzazioni (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare classi LINQ to SQL con mapping a tabelle e visualizzazioni (Progettazione relazionale oggetti)
Le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] di cui viene eseguito il mapping alle tabelle e alle visualizzazioni del database sono chiamate *classi di entità*. La classe di entità esegue il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record.Creare classi di entità basate su tabelle o visualizzazioni di database trascinando quest'ultime da **Esplora server**\/**Esplora database** in [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md).[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] genera le classi e applica gli attributi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] specifici per abilitare le funzionalità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] \(funzionalità di modifica e comunicazione dei dati dell'oggetto <xref:System.Data.Linq.DataContext>\).Per informazioni dettagliate sulle classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], vedere [Il modello a oggetti LINQ to SQL](../Topic/The%20LINQ%20to%20SQL%20Object%20Model.md).  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] rappresenta un'utilità di mapping relazionale a oggetti semplice, poiché supporta solo relazioni di mapping 1:1.In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database.Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato.Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.  
  
## Creazione di classi LINQ to SQL con mapping a tabelle o visualizzazioni di database  
 Il trascinamento di tabelle o visualizzazioni da **Esplora server**\/**Esplora database** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crea classi di entità oltre ai metodi <xref:System.Data.Linq.DataContext> utilizzati per l'esecuzione degli aggiornamenti.  
  
 Per impostazione predefinita, il runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la logica per salvare le modifiche da una classe di entità aggiornabile nel database.Tale logica si basa sullo schema della tabella \(definizioni di colonna e informazioni sulla chiave primaria\).Se non si desidera questo comportamento, è possibile configurare una classe di entità in modo che utilizzi stored procedure per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione anziché utilizzare il comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito.Per ulteriori informazioni, vedere [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database  
  
1.  In **Esplora server**\/**Esplora database** espandere **Tabelle** o **Visualizzazioni** e individuare la tabella o la visualizzazione di database che si desidera utilizzare nell'applicazione.  
  
2.  Trascinare la tabella o la visualizzazione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione.Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.  
  
## Creazione dell'origine dati di un oggetto e visualizzazione dei dati in un form  
 Dopo aver creato classi di entità utilizzando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], è possibile creare l'origine dati di un oggetto e popolare la [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) con le classi di entità.  
  
#### Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL  
  
1.  Scegliere **Compila soluzione** dal menu **Compila** per compilare il progetto.  
  
2.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
3.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
4.  Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto**, quindi su **Avanti**.  
  
5.  Espandere i nodi, quindi individuare e selezionare la classe.  
  
    > [!NOTE]
    >  Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.  
  
6.  Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.  
  
7.  Trascinare gli elementi dalla finestra **Origini dati** in un form.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: creare metodi DataContext con mapping a stored procedure e funzioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Il modello a oggetti LINQ to SQL](../Topic/The%20LINQ%20to%20SQL%20Object%20Model.md)   
 [Procedura: aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md)   
 [Procedura dettagliata: personalizzazione del comportamento di Insert, Update e Delete delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Procedura dettagliata: aggiunta della convalida a classi di entità](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md)   
 [Procedura: creare un'associazione \(relazione\) tra classi LINQ to SQL \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)