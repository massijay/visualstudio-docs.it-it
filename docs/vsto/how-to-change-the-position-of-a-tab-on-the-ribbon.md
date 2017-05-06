---
title: "Procedura: modificare la posizione di una scheda nella barra multifunzione"
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
  - "barra multifunzione [sviluppo per Office in Visual Studio], schede"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Procedura: modificare la posizione di una scheda nella barra multifunzione
  È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione utilizzando l'**Editor della raccolta Tab**.  È possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione.  Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office.  Ad esempio, la scheda **Dati** è una scheda incorporata in Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Per modificare l'ordine delle schede nella barra multifunzione  
  
1.  In **Esplora soluzioni** selezionare il file di codice \(.vb o .cs\) della barra multifunzione.  
  
2.  Scegliere **Finestra di progettazione** dal menu **Visualizza**.  
  
3.  Fare clic con il pulsante destro del mouse sulla finestra di progettazione della barra multifunzione, quindi scegliere **Proprietà**.  
  
4.  Nella finestra **Proprietà** selezionare la proprietà **Tabs**, quindi fare clic sul pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.png "Ellisse di ASP.NET Mobile Designer")\).  
  
     Verrà visualizzato l'**Editor della raccolta Tab**.  
  
5.  Nell'elenco **Membri** dell'**editor della raccolta Tab** selezionare la scheda che si desidera spostare e fare clic sulle frecce in su o in giù per modificare l'ordine delle schede.  
  
### Per posizionare una scheda prima o dopo una scheda incorporata nella barra multifunzione  
  
1.  Selezionare una scheda personalizzata nella finestra di progettazione della barra multifunzione.  
  
2.  Nella finestra **Proprietà**, espandere la proprietà **ControlId** quindi assicurarsi che il valore della proprietà **ControlIdType** sia impostato su **Personalizzata**.  
  
3.  Nella finestra **Proprietà** espandere la proprietà **Position**.  
  
4.  Impostare la proprietà **PositionType** sul valore appropriato:  
  
    -   **BeforeOfficeId** consente di posizionare il gruppo prima di una determinata scheda incorporata.  
  
    -   **AfterOfficeId** consente di posizionare il gruppo dopo una determinata scheda incorporata.  
  
5.  Impostare la proprietà **OfficeId** sull'ID di controllo di una scheda incorporata.  
  
     Per un elenco degli ID di controllo, vedere [File della Guida di Office 2010: Identificatori del controllo fluenti dell'interfaccia utente di Office](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  