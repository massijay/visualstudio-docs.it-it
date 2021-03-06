---
title: 'Procedura: aggiungere controlli alla visualizzazione Backstage | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a16c564b39afdc2ec3cf3e15883fc05b2a13f5d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procedura: aggiungere controlli alla visualizzazione Backstage
  È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic il **File** scheda quando si esegue l'applicazione, i controlli aggiunti per il **File** scheda vengono visualizzati un gruppo denominato  **Componenti aggiuntivi**.  
  
 È possibile posizionare i controlli prima o dopo i controlli incorporati utilizzando la finestra di progettazione della barra multifunzione in Visual Studio. Un controllo incorporato è un controllo che è già presente nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli incorporati, è necessario utilizzare un XML della barra multifunzione. Per ulteriori informazioni su **della barra multifunzione (XML)**, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md). Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere [introduzione per la visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizzazione della visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Per aggiungere controlli alla visualizzazione Backstage  
  
1.  Aprire l'elemento barra multifunzione in visualizzazione progettazione.  
  
     Per informazioni su come aggiungere un **della barra multifunzione (finestra di progettazione visiva)** elemento al progetto, vedere [come: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Nella finestra di progettazione della barra multifunzione, fare clic su di **File** scheda.  
  
     Verrà visualizzata una finestra di progettazione di menu. Questa area di progettazione non contiene tutti i controlli.  
  
3.  Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare uno qualsiasi dei seguenti controlli nella finestra di progettazione dal menu:  
  
    -   Pulsante  
  
    -   CheckBox  
  
    -   Raccolta  
  
    -   Menu  
  
    -   Separatore  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Trascinare i controlli per spostarli in una nuova posizione del menu.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata mediante la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  