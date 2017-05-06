---
title: "Procedura: aggiungere controlli alla visualizzazione Backstage"
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
  - "controlli, barra multifunzione"
  - "barra multifunzione personalizzata, menu"
  - "personalizzazione della barra multifunzione, menu"
  - "menu, personalizzazione"
  - "Microsoft Office (pulsante)"
  - "Microsoft Office (menu)"
  - "Office (pulsante)"
  - "barra multifunzione, personalizzazione"
  - "barra multifunzione, menu"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Procedura: aggiungere controlli alla visualizzazione Backstage
  È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere i controlli al menu visualizzato quando si fa clic sulla scheda **Il file**.  quando si esegue l'applicazione, i controlli aggiunti alla scheda **Il file** in un gruppo denominato **Componenti aggiuntivi**.  
  
 Non è possibile controlli prima o dopo i controlli incorporati utilizzando la finestra di progettazione della barra multifunzione in Visual Studio.  Un controllo incorporato è un controllo già visualizzato nella visualizzazione backstage.  Se si desidera posizionare controlli prima o dopo i controlli incorporati, è necessario utilizzare una barra multifunzione XML.  Per ulteriori informazioni su **Barra multifunzione \(XML\)**, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere [Introduzione alla visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e [Personalizzazione della visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188) \(le pagine potrebbero essere in inglese\).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Per aggiungere controlli alla visualizzazione backstage  
  
1.  Aprire l'elemento della barra multifunzione in visualizzazione Progettazione.  
  
     Per informazioni su come aggiungere un elemento **Barra multifunzione \(finestra di progettazione visiva\)** al progetto, vedere [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Nella finestra di progettazione della barra multifunzione, fare clic sulla scheda **Il file**.  
  
     Viene visualizzata una finestra di progettazione di menu.  In questa area di progettazione non sono contenuti controlli.  
  
3.  Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare uno dei seguenti controlli nella finestra di progettazione di menu:  
  
    -   Button  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   Menu  
  
    -   Separatore  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Trascinare i controlli per spostarli in nuove posizioni nel menu.  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  