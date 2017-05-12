---
title: "Procedura: nascondere i controlli contenuti nei fogli di lavoro durante la stampa"
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
  - "controlli [sviluppo per Office in Visual Studio], nascondere durante la stampa"
  - "stampa [sviluppo per Office in Visual Studio], nascondere controlli"
  - "stampa [sviluppo per Office in Visual Studio], fogli di lavoro"
  - "fogli di lavoro, nascondere controlli durante la stampa"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Procedura: nascondere i controlli contenuti nei fogli di lavoro durante la stampa
  Quando si stampa un documento di Microsoft Office Excel contenente controlli Windows Form, i controlli risulteranno visibili sul foglio di lavoro stampato.  Durante la stampa di un foglio di lavoro è possibile nascondere tali controlli.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Se si nascondono controlli che contengono dati, come ad esempio <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, i dati presenti nel controllo non saranno visibili sul foglio di lavoro stampato.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per nascondere i controlli durante la stampa di un foglio di lavoro  
  
1.  Creare o aprire un progetto di Excel in Visual Studio e verificare che **Sheet1** sia visibile nella finestra di progettazione.  Per informazioni sulla creazione di progetti, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Trascinare un controllo <xref:Microsoft.Office.Tools.Excel.Controls.Button> dalla scheda **Controlli comuni** della **Casella degli strumenti** a una cella in `Sheet1`.  
  
3.  Nella finestra **Proprietà** impostare la proprietà <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> su **False**.  
  
## Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  