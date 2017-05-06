---
title: "Procedura: gestire il layout di controllo dei riquadri delle azioni"
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
  - "riquadri azioni [sviluppo per Office in Visual Studio], layout di controllo"
  - "controlli [sviluppo per Office in Visual Studio], layout in riquadri di azioni"
  - "Smart document [sviluppo per Office in Visual Studio], layout di controllo"
ms.assetid: 857550d0-b9c0-4d2f-a947-dd955bcf2823
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Procedura: gestire il layout di controllo dei riquadri delle azioni
  Per impostazione predefinita, i riquadri delle azioni sono ancorati al lato destro di un documento o di un foglio di lavoro. È tuttavia possibile ancorarli a sinistra, in alto o in basso.  Se si utilizzano più controlli utente, è possibile scrivere codice per impilare in maniera appropriata i controlli utente sul riquadro delle azioni.  Per ulteriori informazioni, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'ordine di presentazione dei controlli varia a seconda che il riquadro delle azioni sia ancorato verticalmente oppure orizzontalmente.  
  
> [!NOTE]  
>  Se l'utente ridimensiona il riquadro delle azioni in fase di esecuzione, è possibile impostare i controlli per il ridimensionamento con il riquadro.  È possibile utilizzare la proprietà <xref:System.Windows.Forms.Control.Anchor%2A> di un controllo Windows Form per ancorare i controlli al riquadro delle azioni.  Per ulteriori informazioni, vedere [Procedura: agganciare i controlli in Windows Form](http://msdn.microsoft.com/library/59ea914f-fbd3-427a-80fe-decd02f7ae6d).  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per impostare l'ordine di presentazione dei controlli riquadro azioni  
  
1.  Aprire un progetto a livello di documento di Microsoft Office Word contenente un riquadro delle azioni con più controlli utente o in cui sono annidati più controlli del riquadro delle azioni.  Per ulteriori informazioni, vedere [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
2.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse su **ThisDocument.cs** o **ThisDocument.vb** e scegliere **Visualizza codice**.  
  
3.  Nel gestore eventi <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> del riquadro delle azioni, verificare se l'orientamento del riquadro delle azioni è orizzontale.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#30)]  
  
4.  Se l'orientamento è orizzontale, ordinare i controlli del riquadro delle azioni partendo da sinistra. In caso contrario, ordinarli partendo dall'alto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#31)]  
  
5.  In C\# è necessario aggiungere un gestore eventi per l'elemento `ActionsPane` al gestore eventi dell'eccezione<xref:Microsoft.Office.Tools.Word.Document.Startup>.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#32)]  
  
6.  Eseguire il progetto e verificare che i controlli del riquadro delle azioni siano ordinati da sinistra a destra quando il riquadro è ancorato alla parte superiore del documento e dall'alto verso il basso quando il riquadro è ancorato al lato destro del documento.  
  
## Esempio  
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#29)]  
  
## Compilazione del codice  
 L'esempio presenta i seguenti requisiti:  
  
-   Un progetto a livello di documento di Word contenente un riquadro delle azioni con più controlli utente o in cui sono annidati più controlli del riquadro delle azioni.  
  
## Vedere anche  
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  