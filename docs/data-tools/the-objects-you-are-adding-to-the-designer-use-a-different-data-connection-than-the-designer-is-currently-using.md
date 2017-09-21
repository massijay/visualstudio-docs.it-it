---
title: "Gli oggetti in corso di aggiunta alla finestra di progettazione utilizzano una connessione dati diversa da quella utilizzata per la finestra di progettazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gli oggetti in corso di aggiunta alla finestra di progettazione utilizzano una connessione dati diversa da quella utilizzata per la finestra di progettazione
Gli oggetti in corso di aggiunta alla finestra di progettazione utilizzano una connessione dati diversa da quella utilizzata per la finestra di progettazione.Sostituire la connessione utilizzata per la finestra di progettazione?  
  
 Quando si aggiungono elementi a [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), tutti gli elementi utilizzano un'unica connessione dati condivisa\(l'area di progettazione rappresenta l'oggetto <xref:System.Data.Linq.DataContext>, che utilizza una sola connessione per tutti gli oggetti nell'area\). Questo messaggio viene visualizzato se si aggiunge alla finestra di progettazione un oggetto che utilizza una connessione dati differente da quella attualmente utilizzata per la finestra di progettazione.Per correggere l'errore, è possibile scegliere di mantenere la connessione esistente.In questo caso, l'oggetto selezionato non verrà aggiunto.In alternativa, è possibile scegliere di aggiungere l'oggetto e reimpostare la connessione di <xref:System.Data.Linq.DataContext> sulla nuova connessione.  
  
> [!NOTE]
>  Se si fa clic su **Sì**, viene eseguito il mapping di tutte le classi di entità in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] alla nuova connessione.  
  
### Per sostituire la connessione esistente con quella utilizzata per l'oggetto selezionato  
  
-   Scegliere **Sì**.  
  
     L'oggetto selezionato viene aggiunto a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]e l'oggetto DataContext.Connection viene impostato sulla nuova connessione.  
  
### Per continuare a utilizzare la connessione esistente e annullare l'aggiunta dell'oggetto selezionato  
  
-   Scegliere **No**.  
  
     L'azione viene annullatae l'oggetto DataContext.Connection resta impostato sulla connessione esistente.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)