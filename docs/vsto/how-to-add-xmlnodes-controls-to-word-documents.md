---
title: "Procedura: aggiungere controlli XMLNode ai documenti di Word"
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
  - "controlli [sviluppo per Office in Visual Studio], aggiunta a documenti"
  - "XMLNodes (controllo), aggiunta a documenti"
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura: aggiungere controlli XMLNode ai documenti di Word
  **importante** le informazioni relative in questo argomento relative a Microsoft Word è verificato esclusivamente per il vantaggio e l'utilizzo degli utenti e le organizzazioni che si trovano fuori dagli Stati Uniti e i relativi territori, o sviluppano programmi eseguiti con prodotti, Microsoft Word che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando È stato rimosso un'implementazione di determinata funzionalità correlata alla classe personalizzata XML da Microsoft Word.  Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli individui o delle organizzazioni che si trovano negli Stati Uniti o nei relativi territori oppure che usano o sviluppano programmi eseguiti con prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010. Questi prodotti funzioneranno in modo diverso rispetto a quelli concessi in licenza prima di tale data oppure acquistati e concessi in licenza per l'uso all'esterno degli Stati Uniti.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Quando si associa un elemento di schema XML ripetuto a un documento di Microsoft Office Word, Visual Studio aggiunge automaticamente un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> al documento.  
  
 Per informazioni sul mapping di elementi di schema XML non ripetuti, vedere [Procedura: aggiungere controlli XMLNode ai documenti di Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Il controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> non è disponibile dalla **Casella degli strumenti** o dalla finestra **Origini dati** e non può essere creato a livello di codice.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Per aggiungere un controllo XMLNode a un documento  
  
1.  Nel documento contenuto nella finestra di progettazione di Visual Studio, fare clic sulla scheda **Sviluppatore** della barra multifunzione.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppo** non è visibile, è necessario prima visualizzarla.  Per ulteriori informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  Nel gruppo **XML**, fare clic su **Schema**.  
  
     Verrà visualizzata la finestra di dialogo **Modelli e aggiunte**.  
  
3.  Fare clic sulla scheda **XML Schema**.  
  
4.  Fare clic su **Aggiungi schema**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi schema**.  
  
5.  Selezionare un XML Schema che contiene elementi di schema ripetuti e fare clic su **Apri**.  
  
     Verrà visualizzata la finestra di dialogo **Impostazioni schema**.  
  
6.  Assegnare un alias o fare clic su **OK** per aggiungere lo schema senza un alias.  
  
     Lo schema verrà aggiunto alla finestra di dialogo **Aggiungi schema**.  
  
7.  Fare clic su **OK** nella finestra di dialogo **Aggiungi schema**.  
  
     Verrà aperto il riquadro attività **Struttura XML**.  
  
8.  Scegliere l'elemento di schema ripetuto nel riquadro attività **Struttura XML** per aggiungere l'elemento al documento.  
  
     Un controllo <xref:Microsoft.Office.Tools.Word.XMLNodes> verrà creato e aggiunto al progetto.  
  
## Vedere anche  
 [Controllo XMLNodes](../vsto/xmlnodes-control.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  