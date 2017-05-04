---
title: "Procedura: determinare l&#39;elemento corrente di Outlook a livello di codice | Microsoft Docs"
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
  - "posta elettronica [sviluppo per Office in Visual Studio], elemento corrente"
  - "elementi di posta elettronica [sviluppo per Office in Visual Studio], corrente"
  - "Outlook [sviluppo per Office in Visual Studio], elemento corrente"
  - "SelectionChange (evento)"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura: determinare l&#39;elemento corrente di Outlook a livello di codice
  In questo esempio viene utilizzato l'evento Explorer.SelectionChange per visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato.  Il codice visualizza quindi l'elemento selezionato.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## Compilazione del codice  
 L'esempio presenta i seguenti requisiti:  
  
-   Elementi appuntamento, contatto e posta elettronica in Microsoft Office Outlook.  
  
## Vedere anche  
 [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: Eseguire la ricerca di un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  