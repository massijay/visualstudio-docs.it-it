---
title: La connessione selezionata utilizza un provider di database non supportate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 956f6ab5180475bf0abb03e4353fe0343f876ae1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La connessione selezionata utilizza un provider di database non supportato
Questo messaggio viene visualizzato quando si trascinano gli elementi che non utilizzano il Provider di dati .NET Framework per SQL Server da **Esplora Server**/**Esplora Database** sul [LINQ to SQL Strumenti di Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] supporta solo connessioni dati che usano il provider di dati .NET Framework per SQL Server. Sono valide solo le connessioni a Microsoft SQL Server o a File di database Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] solo gli elementi delle connessioni dati che usano il provider di dati .NET Framework per SQL Server.  
  
## <a name="see-also"></a>Vedere anche
<xref:System.Data.SqlClient>  
[Messaggi O/R Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
