---
title: "Procedura: inviare messaggi di posta elettronica a livello di codice | Microsoft Docs"
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
  - "posta elettronica [sviluppo per Office in Visual Studio], invio"
  - "elementi di posta elettronica [sviluppo per Office in Visual Studio], invio di posta elettronica"
  - "Outlook [sviluppo per Office in Visual Studio], creazione di posta elettronica"
  - "Outlook [sviluppo per Office in Visual Studio], invio di posta elettronica"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: inviare messaggi di posta elettronica a livello di codice
  In questo esempio viene inviato un messaggio di posta elettronica ai contatti i cui indirizzi di posta elettronica contengono il nome di dominio **example.com**.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## Compilazione del codice  
 L'esempio presenta i seguenti requisiti:  
  
-   Contatti i cui indirizzi di posta elettronica contengano il nome di dominio **example.com**.  
  
## Programmazione efficiente  
 Non rimuovere il codice di filtro che ricerca il nome di dominio **example.com**.  Se si rimuove il filtro, la soluzione invierà messaggi di posta elettronica a tutti i contatti.  
  
## Vedere anche  
 [Utilizzo degli elementi di posta](../vsto/working-with-mail-items.md)   
 [Procedura: Creare un elemento di posta elettronica a livello di codice](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Procedura: accedere ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Procedura: Eseguire azioni quando viene ricevuto un messaggio di posta elettronica a livello di codice](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  