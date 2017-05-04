---
title: "Procedura: eseguire la ricerca in una cartella specifica a livello di codice | Microsoft Docs"
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
  - "Outlook (cartelle) [sviluppo per Office in Visual Studio], ricerca"
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Procedura: eseguire la ricerca in una cartella specifica a livello di codice
  In questo esempio di codice vengono utilizzati i metodi `Find` e `FindNext` per ricercare testo nel campo dell'oggetto dei messaggi di posta elettronica contenuti nella cartella **Posta in arrivo**.  Con questo metodo viene utilizzato un filtro stringa per ricercare la T come lettera iniziale del testo `Subject`.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_OL_SearchFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchFolder/CS/thisaddin.cs#1)]  
  
## Vedere anche  
 [Uso delle cartelle](../vsto/working-with-folders.md)   
 [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  