---
title: "Cenni preliminari sulle propriet&#224; personalizzate dei documenti | Microsoft Docs"
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
  - "_AssemblyLocation (proprietà)"
  - "_AssemblyName (proprietà)"
  - "proprietà personalizzate di documenti"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], proprietà personalizzate"
  - "documenti [sviluppo per Office in Visual Studio], proprietà personalizzate"
  - "documenti Office [sviluppo per Office in Visual Studio], proprietà personalizzate"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Cenni preliminari sulle propriet&#224; personalizzate dei documenti
  Quando si compila un progetto a livello di documento, in Visual Studio vengono aggiunte due proprietà personalizzate al documento nel progetto: \_AssemblyLocation e \_AssemblyName.  Quando un utente apre un documento, l'applicazione di Microsoft Office verifica la presenza di queste proprietà di documento personalizzate.  Se tale verifica ha esito positivo, l'applicazione carica il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] il quale a sua volta avvia la personalizzazione.  Per ulteriori informazioni, vedere [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 Questa proprietà contiene il valore CLSID di un'interfaccia del caricatore della soluzione Office del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Il valore CLSID è 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B.  Non modificare mai questo valore.  
  
## \_AssemblyLocation  
 Questa proprietà contiene una stringa che fornisce dettagli sul manifesto di distribuzione della personalizzazione.  Per ulteriori informazioni sui manifesti, vedere [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Il formato del valore della proprietà \_AssemblyLocation varia a seconda della modalità di distribuzione della soluzione:  
  
-   Se la soluzione viene pubblicata per essere installata da un sito Web, da un percorso UNC o da un'unità CD o USB, la proprietà \_AssemblyLocation presenta il formato *DeploymentManifestPath*|*SolutionID*.  Ad esempio:  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   Durante l'esecuzione o il debug della soluzione in Visual Studio, la proprietà \_AssemblyLocation presenta il formato *DeploymentManifestName*|*SolutionID*|vstolocal.  Ad esempio:  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *SolutionID* è un GUID utilizzato dal [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] per identificare la soluzione.  *SolutionID* viene generato automaticamente quando si compila il progetto. Il termine **vstolocal** indica a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che l'assembly deve essere caricato dalla stessa cartella del documento.  
  
## Vedere anche  
 [Architettura delle soluzioni Office in Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)   
 [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Procedura: pubblicare una soluzione Office utilizzando ClickOnce](http://msdn.microsoft.com/it-it/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Procedura: Creare e modificare proprietà personalizzate di un documento](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  