---
title: "Procedura: impostare i comandi di distribuzione di SharePoint | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, distribuzione"
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedura: impostare i comandi di distribuzione di SharePoint
  Il processo di distribuzione può essere personalizzato impostando comandi pre\-distribuzione e post\-distribuzione.  Questi comandi vengono eseguiti prima e dopo le altre azioni di distribuzione quando si esegue il debug delle soluzioni SharePoint da Visual Studio.  
  
### Per aggiungere un comando pre\-distribuzione  
  
1.  Sulla barra dei menu scegliere **Progetto**, *ProjectName* **Proprietà**.  
  
2.  Scegliere la scheda **SharePoint**.  
  
3.  Nella casella di testo **Riga di comando pre\-distribuzione** digitare i comandi MS\-DOS o MSBuild per personalizzare questo passaggio.  
  
     Ad esempio per elencare il contenuto della directory prima del completamento della distribuzione digitare **dir**.  
  
### Per aggiungere un comando post\-distribuzione  
  
1.  Sulla barra dei menu scegliere **Progetto**, *ProjectName* **Proprietà**.  
  
2.  Scegliere la scheda **SharePoint**.  
  
3.  Nella casella di testo **Riga di comando post\-distribuzione** digitare i comandi MS\-DOS o MSBuild per personalizzare questo passaggio.  
  
     Ad esempio per elencare il contenuto della directory dopo il completamento della distribuzione digitare **dir**.  Per utilizzare una variabile MSBuild per copiare l'assembly dalla directory di compilazione digitare **copy $\(TargetPath\) c:\\DeploymentDirectory**.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  