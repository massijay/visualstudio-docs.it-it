---
title: "Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel | Microsoft Docs"
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
  - "riquadri azioni [sviluppo per Office in Visual Studio], aggiunta di controlli"
  - "riquadri azioni [sviluppo per Office in Visual Studio], creazione in Word"
  - "Smart document [sviluppo per Office in Visual Studio], aggiunta di controlli"
  - "Smart document [sviluppo per Office in Visual Studio], creazione in Word"
ms.assetid: cea3c2b6-9364-4134-b812-50888ad8bd76
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel
  Per aggiungere un riquadro azioni in un documento di Microsoft Office Word o a una cartella di lavoro di Microsoft Excel, creare innanzitutto un controllo utente Windows Form.  Quindi, aggiungere il controllo utente alla proprietà <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> del campo `ThisDocument.ActionsPane` \(Word\) o del campo `ThisWorkbook.ActionsPane` \(Excel\) nel progetto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Creazione del controllo utente  
 Nella procedura seguente viene illustrato come creare un controllo utente in Word o in un progetto Excel.  Aggiunge anche un pulsante al controllo utente che scrive il testo nel documento o la cartella di lavoro quando viene selezionato.  
  
#### Per creare il controllo utente  
  
1.  Aprire il progetto a livello di documento di excel o Word in Visual Studio.  
  
2.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
3.  Fare clic su **Controllo riquadro azioni** nella finestra di dialogo **Aggiungi nuovo elemento**, assegnare al controllo il nome **HelloControl** e fare clic su **Aggiungi**.  
  
    > [!NOTE]  
    >  In alternativa è possibile aggiungere un elemento **Controllo utente** al progetto.  Le classi generate dagli elementi **Controllo riquadro azioni** e **Controllo utente** sono equivalenti a livello funzionale.  
  
4.  Trascinare un controllo **Button** dalla scheda **Windows Form** della **Casella degli strumenti** sul controllo.  
  
    > [!NOTE]  
    >  Se il controllo non è visibile nella finestra di progettazione, fare doppio clic su **HelloControl** in **Esplora soluzioni**.  
  
5.  Aggiungere codice al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante.  Il seguente codice di esempio viene mostrato per un documento di Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/HelloControl.vb#12)]  
  
6.  Per C\#, è necessario aggiungere un gestore eventi per il clic su un pulsante.  È possibile inserire il codice nel costruttore `HelloControl` dopo la chiamata a `IntializeComponent`.  
  
     Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/HelloControl.cs#13)]  
  
## Aggiunta del controllo utente al riquadro delle azioni  
 Per visualizzare il riquadro azioni, aggiungere il controllo utente alla proprietà <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> del campo `ThisDocument.ActionsPane` \(Word\) o del campo `ThisWorkbook.ActionsPane` \(Excel\).  
  
#### Per aggiungere il controllo utente al riquadro delle azioni  
  
1.  Aggiungere il codice seguente alla classe `ThisWorkbook` o `ThisDocument` come dichiarazione a livello di classe \(non aggiungere questo codice a un metodo\).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#14)]  
  
2.  Aggiungere il codice seguente al gestore eventi `ThisDocument_Startup` della classe `ThisDocument` o al gestore eventi `ThisWorkbook_Startup` della classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#15)]  
  
## Vedere anche  
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Procedura: gestire il layout di controllo dei riquadri delle azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  