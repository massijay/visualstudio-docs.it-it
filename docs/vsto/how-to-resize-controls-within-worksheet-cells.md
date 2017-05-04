---
title: "Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro | Microsoft Docs"
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
  - "controlli [sviluppo per Office in Visual Studio], ridimensionamento"
  - "controlli gestiti, ridimensionamento"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], ridimensionamento"
  - "fogli di lavoro, ridimensionamento"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro
  Quando si ridimensionano le colonne o le righe in un foglio di lavoro, i controlli host contenuti nelle celle vengono automaticamente adattati all'altezza o alla larghezza della cella ridimensionata.  I controlli Windows Form non vengono ridimensionati automaticamente per impostazione predefinita.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Se i controlli vengono aggiunti in fase di progettazione, è necessario impostare le opzioni di posizionamento per ciascun controllo.  
  
 Se si aggiunge un controllo Windows Form a livello di codice e si fornisce un argomento di intervallo, il controllo viene ridimensionato automaticamente quando una cella all'interno dell'intervallo viene ridimensionata.  Per ulteriori informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Ridimensionamento di controlli in fase di progettazione  
  
#### Per fare in modo che i controlli vengano ridimensionati con le celle in fase di progettazione  
  
1.  Dalla **Casella degli strumenti** trascinare un controllo Windows Form in un foglio di lavoro.  
  
2.  Fare clic con il pulsante destro del mouse sul controllo, quindi fare clic su **Formato controllo**.  
  
3.  Fare clic sulla scheda **Proprietà** nella finestra di dialogo **Formato controllo**.  
  
4.  In **Collocazione dell'oggetto**, selezionare l'opzione **Sposta e ridimensiona con le celle** e scegliere **OK**.  
  
     Quando si ridimensiona la cella in cui è contenuto, il controllo viene ridimensionato in base alle dimensioni della cella.  
  
## Ridimensionamento dei controlli in fase di esecuzione  
 Se si aggiunge un controllo Windows Form in fase di progettazione e si passa un oggetto <xref:Microsoft.Office.Interop.Excel.Range> come posizione del controllo, il controllo viene ridimensionato automaticamente quando viene ridimensionata la cella del foglio di lavoro contenente l'intervallo.  
  
#### Per fare in modo che i controlli vengano ridimensionati con le celle in fase di esecuzione  
  
1.  Aggiungere un controllo all'intervallo A1.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     Quando si ridimensiona la cella in cui è contenuto, il controllo viene ridimensionato in base alle dimensioni della cella.  
  
## Reimpostazione della posizione del controllo  
 È possibile reimpostare la posizione e il ridimensionamento del controllo impostando la proprietà `Placement` su uno dei seguenti valori <xref:Microsoft.Office.Interop.Excel.XlPlacement>:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### Per modificare il comportamento di un controllo in modo che non venga ridimensionato o spostato con la cella  
  
1.  Chiamare la proprietà di posizionamento del controllo e impostare il valore su <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedura: nascondere i controlli contenuti nei fogli di lavoro durante la stampa](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  