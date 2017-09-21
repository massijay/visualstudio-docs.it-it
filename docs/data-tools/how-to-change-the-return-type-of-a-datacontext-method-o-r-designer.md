---
title: "Procedura: modificare il tipo restituito di un metodo DataContext (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: modificare il tipo restituito di un metodo DataContext (Progettazione relazionale oggetti)
Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> \(creato in base a una stored procedure o funzione\) varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità \(se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità\).Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente.È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi.Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.  
  
> [!NOTE]
>  Non è possibile ripristinare la restituzione del tipo generato automaticamente da parte dei metodi <xref:System.Data.Linq.DataContext>, che presentano un tipo restituito impostato su una classe di entità, mediante la finestra **Proprietà**.Per ripristinare la restituzione di un tipo generato automaticamente da parte di un metodo <xref:System.Data.Linq.DataContext>, è necessario trascinare nuovamente l'oggetto di database originale in Progettazione relazionale oggetti.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità  
  
1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.  
  
2.  Selezionare **Return Type** nella finestra **Proprietà**, quindi selezionare una classe di entità disponibile nell'elenco **Return Type**.Se la classe di entità desiderata non si trova nell'elenco, aggiungerla o crearla in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] per aggiungerla all'elenco.  
  
3.  Salvare il file .dbml.  
  
### Per modificare nuovamente il tipo restituito di un metodo DataContext da una classe di entità nel tipo generato automaticamente  
  
1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi ed eliminarlo.  
  
2.  Trascinare l'oggetto di database da **Esplora server**\/**Esplora database** in un'area vuota di Progettazione relazionale oggetti.  
  
3.  Salvare il file .dbml.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: creare metodi DataContext con mapping a stored procedure e funzioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)