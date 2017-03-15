---
title: "Procedura: accedere direttamente al database mediante un oggetto TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "database [Visual Basic], accesso con un TableAdapter"
  - "dataset [Visual Basic], aggiunta ai progetti"
  - "DBDirect (metodi)"
  - "GenerateDbDirectMethods (proprietà)"
  - "salvataggio di dati"
  - "TableAdapter.Delete (metodo)"
  - "TableAdapter.GenerateDBDirectMethods (proprietà)"
  - "TableAdapter.Insert (metodo)"
  - "TableAdapter.Update (metodo)"
  - "TableAdapters"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: accedere direttamente al database mediante un oggetto TableAdapter
Oltre a `InsertCommand`, `UpdateCommand` e `DeleteCommand`, gli oggetti TableAdapter vengono creati con metodi che è possibile eseguire direttamente nel database.  Tali metodi \(`TableAdapter.Insert`, `TableAdapter.Update` e `TableAdapter.Delete`\) possono essere chiamati direttamente per la modifica dei dati nel database.  
  
 Se non si desidera creare questi metodi diretti, impostare la proprietà `GenerateDbDirectMethods` dell'oggetto TableAdapter su `false` nella finestra **Proprietà**.  Tutte le query aggiunte a un oggetto TableAdapter oltre alla query principale del TableAdapter sono autonome, ovvero non generano metodi DbDirect.  
  
## Invio diretto dei comandi a un database  
 Chiamare il metodo DbDirect dell'oggetto TableAdapter che esegue l'attività che si sta tentando di portare a termine.  
  
#### Per inserire nuovi record direttamente in un database  
  
-   Chiamare il metodo `Insert` del TableAdapter passando i valori per ciascuna colonna come parametri.  Nella procedura riportata di seguito viene utilizzata come esempio la tabella `Region` del database Northwind.  
  
    > [!NOTE]
    >  Se non è disponibile alcuna istanza, creare un'istanza dell'oggetto TableAdapter da utilizzare.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### Per aggiornare i record direttamente in un database  
  
-   Chiamare il metodo `Update` del TableAdapter passando i valori nuovi e originali per ciascuna colonna come parametri.  
  
    > [!NOTE]
    >  Se non è disponibile alcuna istanza, creare un'istanza dell'oggetto TableAdapter da utilizzare.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### Per eliminare i record direttamente da un database  
  
-   Chiamare il metodo `Delete` del TableAdapter passando i valori per ciascuna colonna come parametri del metodo `Delete`.  In questo esempio viene utilizzata la tabella `Region` del database Northwind.  
  
    > [!NOTE]
    >  Se non è disponibile alcuna istanza, creare un'istanza dell'oggetto TableAdapter da utilizzare.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## Vedere anche  
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Comandi e parametri](../Topic/Commands%20and%20Parameters.md)