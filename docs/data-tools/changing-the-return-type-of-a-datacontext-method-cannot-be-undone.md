---
title: "La modifica del tipo restituito di un metodo DataContext non pu&#242; essere annullata | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La modifica del tipo restituito di un metodo DataContext non pu&#242; essere annullata
La modifica del tipo restituito di un metodo DataContext non può essere annullata.Per ripristinare il tipo generato automaticamente, è necessario trascinare nuovamente l'oggetto da Esplora server\/Esplora database su Progettazione relazionale oggetti.Modificare il tipo restituito?  
  
 Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> varia a seconda della posizione in cui si rilascia l'elemento in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità.Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente.È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi.Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.  
  
### Per modificare il tipo restituito di un metodo DataContext  
  
-   Scegliere **Sì**.  
  
### Per uscire dalla finestra di messaggio e lasciare invariato il tipo restituito  
  
-   Scegliere **No**.  
  
### Per ripristinare il tipo restituito originale dopo la modifica del tipo restituito  
  
1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ed eliminarlo.  
  
2.  Individuare l'elemento in **Esplora server\/Esplora database** e trascinarlo in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito predefinito originale.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: creare metodi DataContext con mapping a stored procedure e funzioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)