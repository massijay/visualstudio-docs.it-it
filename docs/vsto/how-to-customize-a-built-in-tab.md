---
title: "Procedura: personalizzare una scheda incorporata | Microsoft Docs"
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
  - "schede incorporate [sviluppo per Office in Visual Studio]"
  - "barra multifunzione [sviluppo per Office in Visual Studio], schede"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura: personalizzare una scheda incorporata
  È possibile aggiungere gruppi e controlli in una scheda incorporata,  cioè una scheda già presente sulla barra multifunzione di un'applicazione di Microsoft Office.  Ad esempio, la scheda **Dati** è una scheda incorporata in Excel.  Quando si crea un gruppo personalizzato, esso viene visualizzato per ultimo nella scheda, ma è possibile spostarlo in un punto qualsiasi della scheda.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  È possibile aggiungere gruppi in una scheda incorporata, ma non è possibile rimuovere gruppi incorporati da una scheda incorporata.  
  
### Per aggiungere gruppi in una scheda incorporata  
  
1.  Fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione in **Esplora soluzioni**, quindi scegliere **Progettazione visualizzazioni**.  
  
    > [!NOTE]  
    >  Se non viene visualizzato il file di codice della barra multifunzione **Esplora soluzioni**, è necessario aggiungere un **elemento Barra multifunzione** al progetto.  Vedere [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Fare clic con il pulsante destro del mouse su una scheda nella finestra di progettazione della barra multifunzione, quindi scegliere **Proprietà**.  
  
3.  Nella finestra **Proprietà** espandere la proprietà **ControlId**, quindi impostare la proprietà **ControlIdType** su **Office**.  
  
4.  Impostare la proprietà **OfficeId** sull'*ID di controllo* della scheda incorporata che si vuole personalizzare.  
  
     L'ID di controllo è il nome che identifica in modo univoco le schede, i gruppi e i controlli incorporati nelle applicazioni Microsoft Office.  
  
     Per un elenco degli ID di controllo, vedere [File della Guida di Office 2010: identificatori di controllo dell'interfaccia utente Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare i gruppi nella scheda.  
  
    > [!NOTE]  
    >  I gruppi incorporati non sono visualizzati nella finestra di progettazione.  Di conseguenza, l'unico modo per determinare se si sta usando una scheda incorporata consiste nell'esaminare la proprietà **ControlId** della scheda.  
  
### Per posizionare gruppi in una scheda incorporata  
  
1.  Selezionare un gruppo personalizzato nella finestra di progettazione della barra multifunzione.  
  
2.  Nella finestra **Proprietà** espandere la proprietà **Posizione**.  
  
3.  Impostare la proprietà **PositionType** sul valore appropriato:  
  
    -   **BeforeOfficeId** posiziona il gruppo prima di un determinato gruppo incorporato.  
  
    -   **AfterOfficeId** posiziona il gruppo dopo un determinato gruppo incorporato.  
  
4.  Impostare la proprietà **OfficeId** sull'ID di controllo di un gruppo incorporato.  
  
     Per un elenco degli ID di controllo, vedere [File della Guida di Office 2010: identificatori di controllo dell'interfaccia utente Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  