---
title: "Procedura: associare una pagina Web a una cartella di Outlook a livello di codice"
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
  - "cartelle [sviluppo per Office in Visual Studio], pagine Web"
  - "Outlook [sviluppo per Office in Visual Studio], pagine Web allegate a cartelle"
  - "pagine Web [sviluppo per Office in Visual Studio], cartelle di Outlook"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: associare una pagina Web a una cartella di Outlook a livello di codice
  In questo esempio viene ricercata una cartella denominata `HtmlView` in Microsoft Office Outlook.  Se la cartella non esiste, nel codice verrà creata la cartella e le verrà assegnata una pagina Web.  Se invece la cartella esiste, il codice ne visualizzerà il contenuto.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## Vedere anche  
 [Uso delle cartelle](../vsto/working-with-folders.md)   
 [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: creare cartelle personalizzate a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  