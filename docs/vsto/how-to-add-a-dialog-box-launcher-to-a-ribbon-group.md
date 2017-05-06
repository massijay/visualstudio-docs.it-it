---
title: "Procedura: aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione"
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
  - "utilità di avvio di finestre di dialogo [sviluppo per Office in Visual Studio]"
  - "barra multifunzione [sviluppo per Office in Visual Studio], utilità di avvio di finestre di dialogo"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Procedura: aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione
  È possibile aggiungere un pulsante di visualizzazione della finestra di dialogo a qualsiasi gruppo della barra multifunzione.  Un pulsante di visualizzazione della finestra di dialogo è una piccola icona visualizzata in un gruppo.  Gli utenti fanno clic su questa icona per aprire finestre di dialogo o riquadri attività correlati in cui sono disponibili altre opzioni relative al gruppo.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Per aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione  
  
1.  In **Esplora soluzioni** selezionare il file di codice \(.vb o .cs\) della barra multifunzione.  
  
2.  Scegliere **Finestra di progettazione** dal menu **Visualizza**.  
  
3.  Nella finestra di progettazione della barra multifunzione fare clic con il pulsante destro del mouse su un gruppo, quindi scegliere **Aggiungi DialogBoxLauncher**.  
  
     Aggiungere codice all'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> del gruppo per aprire una finestra di dialogo personalizzata o incorporata.  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  