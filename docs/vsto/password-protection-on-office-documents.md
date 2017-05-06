---
title: "Sicurezza tramite password di documenti di Office"
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
  - "documenti [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "documenti Office [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "password [sviluppo per Office in Visual Studio], protezioni di documenti"
  - "autorizzazioni [sviluppo per Office in Visual Studio]"
  - "cartelle di lavoro [sviluppo per Office in Visual Studio], autorizzazioni limitate"
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Sicurezza tramite password di documenti di Office
  È possibile impostare una password nei documenti di Microsoft Office Word e nelle cartelle di lavoro di Microsoft Office Excel per impedirne l'apertura da parte di utenti non autorizzati.  Questa opzione è chiamata **Password all'apertura**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 È possibile creare progetti a livello di documento utilizzando documenti e cartelle di lavoro esistenti con l'opzione **Password all'apertura** abilitata.  Il comportamento dei documenti di Word e Excel che utilizzano l'opzione **Password all'apertura** è diverso in Visual Studio.  
  
 Per informazioni sull'attivazione dell'opzione **Password all'apertura**, consultare la Guida di Word o Excel.  
  
## Comportamento di Excel e Word  
 Ogni volta che in Visual Studio si apre una cartella di lavoro di Excel con l'opzione **Password all'apertura** attivata, viene richiesta la password.  Quando si compila la soluzione viene nuovamente richiesta la password, in quando il documento viene aperto durante la compilazione.  
  
 La prima volta che in Visual Studio si apre un documento di Word con l'opzione **Password all'apertura** attivata, viene richiesta la password.  Dopo aver immesso la password corretta, l'opzione **Password all'apertura** viene rimossa dal documento e non è più necessario specificare la password.  Se si desidera che all'apertura del documento della soluzione venga richiesta una password, attivare l'opzione **Password all'apertura** dopo la compilazione finale e prima della distribuzione della soluzione.  
  
## Vedere anche  
 [Sicurezza dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Cenni preliminari sul servizio Information Rights Management e sulle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Procedura: supportare l'esecuzione di codice sottostante i documenti con autorizzazioni limitate](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  