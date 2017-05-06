---
title: "Procedura: aggiungere un riquadro attivit&#224; personalizzato a un&#39;applicazione"
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
  - "riquadri attività personalizzati [sviluppo per Office in Visual Studio], aggiunta ad applicazioni"
  - "riquadri attività [sviluppo per Office in Visual Studio], aggiunta ad applicazioni"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura: aggiungere un riquadro attivit&#224; personalizzato a un&#39;applicazione
  È possibile aggiungere un riquadro attività personalizzato alle applicazioni elencate sopra usando un componente aggiuntivo VSTO.  Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso.  La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Aggiunta di un riquadro attività personalizzato a un'applicazione  
  
#### Per aggiungere un riquadro attività personalizzato a un'applicazione  
  
1.  Aprire o creare un progetto di componente aggiuntivo VSTO per una delle applicazioni elencate sopra.  Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** modificare il nome del nuovo controllo utente in **MyUserControl** e quindi fare clic su **Aggiungi**.  
  
     Il controllo utente viene visualizzato nella finestra di progettazione.  
  
4.  Aggiungere uno o più controlli Windows Form dalla **Casella degli strumenti** al controllo utente.  
  
5.  Aprire il file di codice **ThisAddIn.cs** o **ThisAddIn.vb**.  
  
6.  Aggiungere il codice seguente alla classe `ThisAddIn`.  Questo codice dichiara le istanze di `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> come membri della classe `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  Aggiungere il codice seguente al gestore eventi `ThisAddIn_Startup`.  Questo codice crea un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> aggiungendo l'oggetto `MyUserControl` alla raccolta `CustomTaskPanes`.  Il codice visualizza anche il riquadro attività.  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  Questo codice associa il riquadro attività alla finestra attiva nell'applicazione.  Per alcune applicazioni, si potrebbe voler modificare il codice perché il riquadro attività venga visualizzato con altri documenti o elementi nell'applicazione.  Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
## Vedere anche  
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Riquadri attività personalizzati](../vsto/custom-task-panes.md)   
 [Procedura dettagliata: automazione di un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  