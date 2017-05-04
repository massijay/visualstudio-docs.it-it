---
title: "Procedura: aprire soluzioni Office senza eseguire codice | Microsoft Docs"
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
  - "assembly [sviluppo per Office in Visual Studio], esclusione"
  - "esclusione di assembly"
  - "documenti [sviluppo per Office in Visual Studio], apertura senza eseguire il codice"
  - "documenti Office [sviluppo per Office in Visual Studio], apertura senza eseguire il codice"
  - "Soluzioni Office [sviluppo per Office in Visual Studio], apertura"
  - "apertura di soluzioni Office"
  - "soluzioni [sviluppo per Office in Visual Studio], apertura"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: aprire soluzioni Office senza eseguire codice
  Una soluzione Microsoft Office creata con estensioni di codice gestito viene eseguita anche se il livello di sicurezza nell'applicazione di Office dell'utente finale è impostato su Elevato.  Ciò accade perché la sicurezza del codice dell'assembly .NET è gestita da Microsoft .NET Framework, non da Microsoft Office.  
  
 In alcuni casi, tuttavia, potrebbe essere necessario aprire un documento senza eseguire il codice.  Ad esempio quando si desidera aggiornare l'aspetto di un documento prima che il codice lo modifichi, poiché il codice eseguito durante l'apertura del documento potrebbe alterarne il contenuto,  oppure quando si desidera inviare a un utente un documento con determinate informazioni senza che il codice venga eseguito e le alteri.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Esistono diversi modi per aprire un documento o una cartella di lavoro contenente estensioni di codice gestito senza eseguire il codice dell'assembly.  
  
### Per ignorare l'assembly premendo MAIUSC  
  
-   Aprire documenti e cartelle di lavoro dal menu **File** tenendo premuto MAIUSC per impedire la generazione di eventi di inizializzazione da parte di Word e Excel mentre viene aperto il documento.  
  
    > [!NOTE]  
    >  Se si apre un documento o una cartella di lavoro dal riquadro attività della **Guida introduttiva**, tenendo premuto MAIUSC il codice non viene ignorato.  Inoltre, tenendo premuto MAIUSC non si impedisce la generazione di eventi dopo l'apertura del documento.  
  
     Questo metodo si rivela utile se si desidera aprire un documento per effettuare modifiche senza che il codice venga eseguito e modifichi il documento per primo.  
  
### Per ignorare un assembly rinominandolo o rimuovendolo  
  
-   Se sul computer in cui si trova l'assembly si dispone delle autorizzazioni necessarie, sarà possibile rinominare o rimuovere l'assembly per impedire al documento o alla cartella di lavoro di trovarlo.  In questo modo viene generato un errore ogni volta che viene aperto il documento di Office.  
  
     Se la soluzione è utilizzata da più persone, questo metodo ne impedirà l'utilizzo da parte di tutti gli utenti.  Questo può essere utile se viene identificato un problema nel codice o in un server a cui si fa riferimento e si desidera impedire a tutti gli utenti di eseguirlo.  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifesti dell'applicazione e di distribuzione nelle soluzioni Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  