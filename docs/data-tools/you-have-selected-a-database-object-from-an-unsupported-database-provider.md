---
title: "&#200; stato selezionato un oggetto di database da un provider del database non supportato | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# &#200; stato selezionato un oggetto di database da un provider del database non supportato
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) supporta solo il provider di dati .NET Framework per SQL Server \(<xref:System.Data.SqlClient>\).Anche se è possibile fare clic su **OK** e continuare a utilizzare gli oggetti di provider del database non supportati, potrebbe verificarsi un comportamento imprevisto in fase di esecuzione.  
  
> [!NOTE]
>  Sono supportate solo connessioni dati che utilizzano il provider di dati .NET Framework per SQL Server.  
  
### Per correggere l'errore  
  
-   Fare clic su **OK** per continuare a progettare le classi di entità con mapping alla connessione che utilizza il provider del database non supportato.Quando si utilizzano provider del database non supportati, potrebbe verificarsi un comportamento imprevisto.  
  
     \-oppure\-  
  
-   Fare clic su **Annulla**.  
  
     L'azione viene interrotta.Creare o utilizzare una connessione dati che si avvale del provider .NET Framework per SQL Server.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Provider di dati .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)