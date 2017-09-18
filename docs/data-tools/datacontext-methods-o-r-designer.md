---
title: "Metodi DataContext (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Metodi DataContext (Progettazione relazionale oggetti)
I metodi <xref:System.Data.Linq.DataContext> \(nel contesto di [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)\) rappresentano metodi della classe <xref:System.Data.Linq.DataContext> che eseguono stored procedure e funzioni in un database.  
  
 La classe <xref:System.Data.Linq.DataContext> rappresenta una classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] che funge da canale tra un database SQL Server e le classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping a tale database.Nella classe <xref:System.Data.Linq.DataContext> sono contenute le informazioni della stringa di connessione e i metodi per la connessione a un database e per la modifica dei dati nel database. Per impostazione predefinita, nella classe <xref:System.Data.Linq.DataContext> sono contenuti diversi metodi che è possibile chiamare, come ad esempio il metodo <xref:System.Data.Linq.DataContext.SubmitChanges%2A> che invia i dati aggiornati dalle classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] al database.È anche possibile creare metodi <xref:System.Data.Linq.DataContext> aggiuntivi con mapping a stored procedure e funzioni.In altre parole, la chiamata a questi metodi personalizzati determinerà l'esecuzione della stored procedure o funzione nel database a cui è stato eseguito il mapping del metodo <xref:System.Data.Linq.DataContext>.È possibile aggiungere nuovi metodi alla classe <xref:System.Data.Linq.DataContext> nello stesso modo in cui si aggiungono per estendere qualsiasi classe.Tuttavia, quando si considerano i metodi <xref:System.Data.Linq.DataContext> nel contesto di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], si intendono fondamentalmente i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni.  
  
> [!NOTE]
>  In [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] le stored procedure e le funzioni vengono gestite nello stesso modo, nel senso che viene eseguito il mapping di entrambe alle classi di entità utilizzando lo stesso oggetto <xref:System.Data.Linq.StoredProcedureAttribute>.Nel contesto di [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)], i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure sono gli stessi di quelli con mapping a funzioni.  
  
## Riquadro Metodi  
 I metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni vengono visualizzati nel riquadro dei metodi di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Il riquadro dei metodi rappresenta il riquadro situato sul lato del riquadro delle entità \(l'area di progettazione principale\).Nel riquadro dei metodi vengono elencati tutti i metodi <xref:System.Data.Linq.DataContext> creati utilizzando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Per impostazione predefinita, il riquadro dei metodi è vuoto. Trascinare stored procedure o funzioni da **Esplora server**\/**Esplora database** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] per creare metodi <xref:System.Data.Linq.DataContext> e popolare il riquadro dei metodi.Per ulteriori informazioni, vedere [Procedura: creare metodi DataContext con mapping a stored procedure e funzioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Per aprire e chiudere il riquadro dei metodi, fare clic con il pulsante destro del mouse su [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], quindi fare clic su **Nascondi riquadro Metodi** o **Mostra riquadro Metodi** oppure utilizzare il tasto di scelta rapida CTRL\+1.  
  
## Due tipi di metodi DataContext  
 I metodi DataContext sono metodi con mapping a stored procedure e funzioni nel database.È possibile creare e aggiungere metodi DataContext nel riquadro dei metodi di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Esistono due tipi distinti di metodi <xref:System.Data.Linq.DataContext>: quelli che restituiscono uno o più set di risultati e quelli che non restituiscono alcun set di risultati.  
  
-   Metodi <xref:System.Data.Linq.DataContext> che restituiscono uno o più set di risultati:  
  
     Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure e funzioni nel database e restituire i risultati.Per ulteriori informazioni, vedere [Procedura: creare metodi DataContext con mapping a stored procedure e funzioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), <xref:System.Data.Linq.ISingleResult%271> e <xref:System.Data.Linq.IMultipleResults>.  
  
-   Metodi <xref:System.Data.Linq.DataContext> che non restituiscono set di risultati, ad esempio inserimenti, aggiornamenti ed eliminazioni per una classe di entità specifica.  
  
     Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure anziché utilizzare il comportamento [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito per salvare i dati modificati tra una classe di entità e il database.Per ulteriori informazioni, vedere [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## Tipi restituiti dei metodi DataContext  
 Quando si trascinano stored procedure e funzioni da **Esplora server**\/**Esplora database** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], il tipo restituito del metodo <xref:System.Data.Linq.DataContext> generato varia a seconda della posizione in cui si rilascia l'elemento.Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, mentre il rilascio degli elementi in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] \(in uno dei riquadri\) crea un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente.Questo tipo creato è dotato di un nome corrispondente a quello della stored procedure o funzione e di proprietà con mapping ai campi restituiti dalla stored procedure o funzione.  
  
> [!NOTE]
>  È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi.Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**.Per ulteriori informazioni, vedere [Procedura: modificare il tipo restituito di un metodo DataContext \(Progettazione relazionale oggetti\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Gli oggetti trascinati dal database nell'area Progettazione relazionale oggetti vengono denominati automaticamente, in base al nome degli oggetti nel database.Se si trascina più volte lo stesso oggetto, i vari nomi vengono distinti grazie all'aggiunta di un numero alla fine del nuovo nome.Se i nomi degli oggetti di database contengono spazi o caratteri non supportati in Visual Basic o C\#, lo spazio o il carattere non valido viene sostituito con un carattere di sottolineatura.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Stored procedure](../Topic/Stored%20Procedures.md)   
 [Procedura: creare metodi DataContext con mapping a stored procedure e funzioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Procedura dettagliata: personalizzazione del comportamento di Insert, Update e Delete delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)