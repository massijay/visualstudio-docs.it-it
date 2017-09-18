---
title: "Procedura: creare metodi DataContext con mapping a stored procedure e funzioni (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare metodi DataContext con mapping a stored procedure e funzioni (Progettazione relazionale oggetti)
È possibile aggiungere stored procedure e funzioni a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] come metodi <xref:System.Data.Linq.DataContext>.La chiamata al metodo e il passaggio dei parametri obbligatori comportano l'esecuzione della stored procedure o funzione nel database e la restituzione dei dati nel tipo restituito del metodo <xref:System.Data.Linq.DataContext>.Per informazioni dettagliate sui metodi <xref:System.Data.Linq.DataContext>, vedere [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Le stored procedure possono essere utilizzate anche per eseguire l'override del comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database.Per ulteriori informazioni, vedere [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Creazione di metodi DataContext  
 È possibile creare metodi <xref:System.Data.Linq.DataContext> trascinando stored procedure o funzioni da **Esplora server\/Esplora database** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  Il tipo restituito del metodo <xref:System.Data.Linq.DataContext> generato varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità,mentre il rilascio degli elementi in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crea un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente.È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi.Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**.Per ulteriori informazioni, vedere [Procedura: modificare il tipo restituito di un metodo DataContext \(Progettazione relazionale oggetti\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per creare metodi DataContext che restituiscono tipi generati automaticamente  
  
1.  In **Esplora server**\/**Esplora database** espandere il nodo **Stored procedure** del database utilizzato.  
  
2.  Individuare la stored procedure desiderata e trascinarla in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Il metodo <xref:System.Data.Linq.DataContext> viene creato con un tipo restituito generato automaticamente e viene visualizzato nel riquadro **Metodi**.  
  
#### Per creare metodi DataContext con il tipo restituito di una classe di entità  
  
1.  In **Esplora server**\/**Esplora database** espandere il nodo **Stored procedure** del database utilizzato.  
  
2.  Individuare la stored procedure desiderata e trascinarla in una classe di entità esistente di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Il metodo <xref:System.Data.Linq.DataContext> viene creato con il tipo restituito della classe di entità selezionata e viene visualizzato nel riquadro **Metodi**.  
  
> [!NOTE]
>  Per informazioni sulla modifica del tipo restituito dei metodi <xref:System.Data.Linq.DataContext> esistenti, vedere [Procedura: modificare il tipo restituito di un metodo DataContext \(Progettazione relazionale oggetti\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Procedura: scrivere query LINQ in C\#](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)