---
title: "Impossibile eliminare la classe selezionata perch&#233; &#232; utilizzata come tipo restituito per uno o pi&#249; metodi DataContext | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Impossibile eliminare la classe selezionata perch&#233; &#232; utilizzata come tipo restituito per uno o pi&#249; metodi DataContext
Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata.L'eliminazione di una classe di entità utilizzata come tipo restituito di un metodo <xref:System.Data.Linq.DataContext> determinerà l'esito negativo della compilazione del progetto.Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'utilizzano e impostare i relativi tipi restituiti su una classe di entità diversa.  
  
 Per ripristinare i tipi generati automaticamente originali dei tipi restituiti dei metodi <xref:System.Data.Linq.DataContext>, eliminare innanzitutto il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi e quindi trascinare nuovamente l'oggetto da **Esplora server**\/**Esplora database** in Progettazione relazionale oggetti.  
  
### Per correggere l'errore  
  
1.  Identificare i metodi <xref:System.Data.Linq.DataContext> che utilizzano la classe di entità come tipo restituito selezionando un metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi e controllando la proprietà **Return Type** nella finestra **Proprietà**.  
  
2.  Impostare **Return Type** su una classe di entità diversa oppure eliminare il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi.  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: modificare il tipo restituito di un metodo DataContext \(Progettazione relazionale oggetti\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)