---
title: "Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio | Microsoft Docs"
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
  - "mapping [sviluppo per Office in Visual Studio], XML Schema a documenti di Word"
  - "Word [sviluppo per Office in Visual Studio], mapping di XML Schema"
  - "XML Schema [sviluppo per Office in Visual Studio], mapping"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio
  **importante** le informazioni relative in questo argomento relative a Microsoft Word è verificato esclusivamente per il vantaggio e l'utilizzo degli utenti e le organizzazioni che si trovano fuori dagli Stati Uniti e i relativi territori, o sviluppano programmi eseguiti con prodotti, Microsoft Word che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando È stato rimosso un'implementazione di determinata funzionalità correlata alla classe personalizzata XML da Microsoft Word.  Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli individui o delle organizzazioni che si trovano negli Stati Uniti o nei relativi territori oppure che usano o sviluppano programmi eseguiti con prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010. Questi prodotti funzioneranno in modo diverso rispetto a quelli concessi in licenza prima di tale data oppure acquistati e concessi in licenza per l'uso all'esterno degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 È possibile effettuare il mapping di uno schema XML a un documento mentre quest'ultimo è aperto in Visual Studio.  Vengono utilizzati gli stessi strumenti di Microsoft Office Word impiegati quando il documento è aperto all'esterno di Visual Studio.  Il progetto di Office crea gli stessi oggetti, indipendentemente dal fatto che venga eseguito il mapping dello schema al documento prima o dopo aver creato la soluzione per Word.  
  
### Per eseguire il mapping di uno schema XML a un documento di Word in Visual Studio  
  
1.  Aprire il progetto relativo al documento o al modello di Word in Visual Studio.  
  
2.  Fare clic nel documento per attivare la finestra di progettazione.  
  
3.  Sulla barra multifunzione, fare clic sulla scheda **Sviluppo**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppo** non è visibile, è necessario prima visualizzarla.  Per ulteriori informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Nel gruppo **XML**, fare clic su **Schema**.  
  
     Verrà visualizzata la finestra di dialogo **Modelli e aggiunte**.  
  
5.  Fare clic sulla scheda **XML Schema**.  
  
6.  Fare clic su **Aggiungi schema**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi schema**.  
  
7.  Individuare il file di schema, selezionarlo e fare clic su **Apri**.  
  
     Verrà visualizzata la finestra di dialogo **Impostazioni schema**.  
  
8.  Assegnare un alias o fare clic su **OK** per aggiungere lo schema senza un alias.  
  
9. Fare clic su **OK**.  
  
     Verrà visualizzata la finestra **Struttura XML**.  
  
10. Trascinare gli elementi dalla finestra **Struttura XML** sui punti del documento in cui si desidera creare i corrispondenti controlli.  
  
## Vedere anche  
 [Procedura: mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  