---
title: "La connessione selezionata utilizza un provider del database non supportato | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La connessione selezionata utilizza un provider del database non supportato
Questo messaggio viene visualizzato quando si trascinano elementi, che non utilizzano il provider di dati .NET Framework per SQL Server, da **Esplora server**\/**Esplora database** in [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] supporta solo connessioni dati che utilizzano il provider di dati .NET Framework per SQL Server.Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.  
  
### Per correggere l'errore  
  
-   Aggiungere a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] solo gli elementi delle connessioni dati che utilizzano il provider di dati .NET Framework per SQL Server.  
  
## Vedere anche  
 <xref:System.Data.SqlClient>   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/it-it/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [Provider di dati .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Creazione di applicazioni dati](../data-tools/creating-data-applications.md)