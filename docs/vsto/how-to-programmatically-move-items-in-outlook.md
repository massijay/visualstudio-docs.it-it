---
title: "Procedura: spostare elementi in Outlook a livello di codice"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook (cartelle) [sviluppo per Office in Visual Studio], spostamento di elementi"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: spostare elementi in Outlook a livello di codice
  In questo esempio i messaggi di posta elettronica non letti vengono spostati dalla cartella **Posta in arrivo** in una cartella denominata **Test**.  Nell'esempio vengono spostati solo i messaggi che contengono la parola **Test** nel campo `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## Compilazione del codice  
 L'esempio presenta i seguenti requisiti:  
  
-   Una cartella di posta di Outlook denominata **Test**.  
  
-   Un messaggio di posta elettronica in arrivo contenente la parola **Test** nel campo `Subject`.  
  
## Vedere anche  
 [Uso delle cartelle](../vsto/working-with-folders.md)   
 [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: eseguire la ricerca in una cartella specifica a livello di codice](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Procedura: Eseguire azioni quando viene ricevuto un messaggio di posta elettronica a livello di codice](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  