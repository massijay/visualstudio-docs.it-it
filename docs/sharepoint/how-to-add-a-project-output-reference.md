---
title: "Procedura: aggiungere un riferimento all&#39;output del progetto"
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
  - "riferimenti all'output del progetto [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, strumenti di creazione di pacchetti avanzati"
  - "sviluppo per SharePoint in Visual Studio, riferimenti all'output del progetto"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: aggiungere un riferimento all&#39;output del progetto
  Per distribuire in SharePoint assembly di progetti non SharePoint o file con estensione xap di progetti Silverlight, aggiungerli come riferimento all'output del progetto.  
  
 Questo processo comporta la creazione di una dipendenza del processo di compilazione della soluzione tra i due progetti.  I progetti associati ai riferimenti all'output del progetto vengono compilati prima della compilazione e della distribuzione del progetto SharePoint.  
  
### Per aggiungere un riferimento all'output del progetto  
  
1.  Caricare una soluzione contenente almeno un progetto SharePoint e un progetto non SharePoint.  
  
2.  In **Esplora soluzioni**, scegliere un elemento nel nodo di progetto SharePoint.  
  
3.  Nella finestra **Proprietà**, scegliere la proprietà **Riferimenti all'output del progetto**, quindi scegliere il bottone accanto ad essa con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/docs/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\).  
  
4.  Nella finestra di dialogo **Riferimenti all'output del progetto**, scegliere il bottone **Aggiungi**.  
  
5.  Nel riquadro delle proprietà, scegliere la freccia accanto la proprietà **Tipo distribuzione** e selezionare un valore adatto per l'elemento non\-SharePoint a cui si fa riferimento, ad esempio **ElementFile**.  
  
6.  Scegliere la freccia accanto a **Nome progetto**, scegliere il nome dell'elemento del progetto non\-SharePoint e quindi scegliere il pulsante di **OK**.  
  
## Vedere anche  
 [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  