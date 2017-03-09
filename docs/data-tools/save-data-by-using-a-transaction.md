---
title: "Procedura: salvare dati utilizzando una transazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], salvataggio"
  - "salvataggio di dati, utilizzo di transazioni"
  - "System.Transactions (spazio dei nomi)"
  - "transazioni, salvataggio di dati"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: salvare dati utilizzando una transazione
I dati vengono salvati in una transazione utilizzando lo spazio dei nomi <xref:System.Transactions>.  Utilizzare l'oggetto <xref:System.Transactions.TransactionScope> per prendere parte a una transazione gestita in modo automatico per questa procedura.  
  
 I progetti non vengono creati con un riferimento all'assembly System.Transactions; pertanto, è necessario aggiungere manualmente un riferimento ai progetti che utilizzano le transazioni.  
  
> [!NOTE]
>  Lo spazio dei nomi <xref:System.Transactions> è supportato da Windows 2000 e versioni successive.  
  
 Il modo più semplice per implementare una transazione consiste nella creazione di un'istanza di un oggetto <xref:System.Transactions.TransactionScope> in un'istruzione `using`.  Per ulteriori informazioni, vedere [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) e [Istruzione using](/dotnet/csharp/language-reference/keywords/using-statement). Il codice eseguito all'interno dell'istruzione `using` prenderà parte alla transazione.  
  
 Per eseguire il commit della transazione, chiamare il metodo <xref:System.Transactions.TransactionScope.Complete%2A> come ultima istruzione nel blocco di utilizzo.  
  
 Per eseguire il rollback della transazione, generare un'eccezione prima di chiamare il metodo <xref:System.Transactions.TransactionScope.Complete%2A>.  
  
 Per ulteriori informazioni, vedere [Procedura dettagliata: salvataggio di dati in una transazione](../data-tools/save-data-in-a-transaction.md).  
  
### Per aggiungere un riferimento all'oggetto dll System.Transactions  
  
1.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
2.  Selezionare **System.Transactions** nella scheda **.NET** \(scheda **SQL Server** per progetti SQL Server\) e scegliere **OK**.  
  
     Nel progetto viene aggiunto un riferimento all'oggetto System.Transactions.dll.  
  
### Per salvare i dati in una transazione  
  
-   Aggiungere il codice per salvare i dati all'interno dell'istruzione di utilizzo in cui è contenuta la transazione.  Nel codice riportato di seguito viene illustrato come creare un oggetto <xref:System.Transactions.TransactionScope> e la relativa istanza in un'istruzione di utilizzo:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## Vedere anche  
 [Procedura dettagliata: salvataggio di dati in una transazione](../data-tools/save-data-in-a-transaction.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)