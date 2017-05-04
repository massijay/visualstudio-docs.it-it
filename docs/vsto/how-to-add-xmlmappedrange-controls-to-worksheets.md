---
title: "Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro | Microsoft Docs"
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
  - "controlli [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro"
  - "XMLMappedRange (controllo), aggiunta a fogli di lavoro"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Procedura: aggiungere controlli XMLMappedRange a fogli di lavoro
  Quando si associa un elemento XML a una cella in Microsoft Office Excel, Visual Studio aggiunge automaticamente un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> al foglio di lavoro.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> non è disponibile nella **Casella degli strumenti** o nella finestra **Origini dati**.  Inoltre, non è possibile creare controlli <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a livello di codice.  
  
### Per aggiungere un controllo XMLMappedRange a un foglio di lavoro  
  
1.  Aprire la cartella di lavoro di Excel nella finestra di progettazione di Visual Studio.  
  
2.  Aprire la cartella di lavoro in cui si desidera aggiungere il controllo.  
  
3.  Nella scheda **Sviluppo** fare clic su **Origine**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non è visibile sulla barra multifunzione, è necessario attivarla.  Per ulteriori informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Verrà visualizzato il riquadro attività **Origine XML**.  
  
4.  Scegliere **XML Maps** nel riquadro attività **Origine XML**.  
  
5.  Fare clic su **Aggiungi** nella finestra di dialogo **XML Maps**.  
  
     Verrà visualizzata la finestra di dialogo **Origine XML**.  
  
6.  Selezionare uno schema XML dalla finestra di dialogo **Origine XML** e fare clic su **Apri**.  
  
     Lo schema verrà aggiunto alla finestra di dialogo **XML Maps**.  
  
7.  Fare clic su **OK** nella finestra di dialogo **XML Maps**.  
  
8.  Trascinare un elemento dal riquadro attività **Origine XML** su una cella del foglio di lavoro.  
  
     Verrà creato un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> e aggiunto al progetto.  
  
    > [!NOTE]  
    >  Se si trascina un elemento padre dal riquadro attività **Origine XML**, verrà creato un controllo <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## Vedere anche  
 [Controllo XmlMappedRange](../vsto/xmlmappedrange-control.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Procedura: mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  