---
title: "Procedura dettagliata: Sincronizzazione di un riquadro attivit&#224; personalizzato con una barra multifunzione"
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
  - "riquadri attività personalizzati [sviluppo per Office in Visual Studio], visualizzare e nascondere"
  - "visualizzazione di riquadri attività personalizzati"
  - "barra multifunzione [sviluppo per Office in Visual Studio], riquadri attività personalizzati"
  - "interruttori [sviluppo per Office in Visual Studio]"
  - "riquadri attività personalizzati [sviluppo per Office in Visual Studio], sincronizzazione con pulsante della barra multifunzione"
  - "interfacce utente [sviluppo per Office in Visual Studio], riquadri attività personalizzati"
  - "sincronizzazione [sviluppo per Office in Visual Studio], riquadri attività personalizzati"
  - "riquadri attività [sviluppo per Office in Visual Studio], visualizzare e nascondere"
  - "riquadri attività personalizzati [sviluppo per Office in Visual Studio], creazione"
  - "nascondere riquadri attività personalizzati"
  - "riquadri attività [sviluppo per Office in Visual Studio], creazione"
  - "riquadri attività [sviluppo per Office in Visual Studio], sincronizzazione con pulsante della barra multifunzione"
ms.assetid: 00ce8b1e-1370-42f2-9dc9-609cada392f1
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura dettagliata: Sincronizzazione di un riquadro attivit&#224; personalizzato con una barra multifunzione
  Questa procedura dettagliata illustra come creare un riquadro attività personalizzato che gli utenti possono nascondere o visualizzare facendo clic su un interruttore nella barra multifunzione. È consigliabile creare sempre un elemento dell'interfaccia utente, ad esempio un pulsante, che gli utenti possono usare per visualizzare o nascondere il riquadro attività personalizzato, perché le applicazioni di Microsoft Office non forniscono una modalità predefinita per visualizzare o nascondere i riquadri attività personalizzati.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Benché questa procedura dettagliata usi Excel in modo specifico, i concetti illustrati sono applicabili a tutte le applicazioni elencate in precedenza.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Progettazione dell'interfaccia utente del riquadro attività personalizzato.  
  
-   Aggiunta di un interruttore alla barra multifunzione.  
  
-   Sincronizzazione dell'interruttore con il riquadro attività personalizzato.  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel o Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].  
  
## Creazione del progetto di componente aggiuntivo  
 In questo passaggio, verrà creato un progetto di componente aggiuntivo VSTO per Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto di componente aggiuntivo per Excel con il nome **SynchronizeTaskPaneAndRibbon**, usando il modello di progetto di componente aggiuntivo per Excel. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice **ThisAddIn.cs** o **ThisAddIn.vb** e aggiunge il progetto **SynchronizeTaskPaneAndRibbon** a **Esplora soluzioni**.  
  
## Aggiunta di un interruttore alla barra multifunzione  
 Per la progettazione di applicazioni di Office, è necessario che gli utenti abbiano sempre il controllo dell'interfaccia utente dell'applicazione di Office. Per permettere agli utenti di controllare il riquadro attività personalizzato, è possibile aggiungere un interruttore della barra multifunzione che consente di visualizzare e nascondere il riquadro attività. Per creare un interruttore, aggiungere un elemento **Barra multifunzione \(finestra di progettazione visiva\)** al progetto. La finestra di progettazione consente di aggiungere e posizionare controlli, impostarne le proprietà e gestirne gli eventi. Per altre informazioni, vedere [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md).  
  
#### Per aggiungere un interruttore alla barra multifunzione  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione \(finestra di progettazione visiva\)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **ManageTaskPaneRibbon** e fare clic su **Aggiungi**.  
  
     Il file **ManageTaskPaneRibbon.cs** o **ManageTaskPaneRibbon.vb** si apre nella finestra di progettazione della barra multifunzione e visualizza una scheda e un gruppo predefiniti.  
  
4.  Nella finestra di progettazione della barra multifunzione fare clic su **group1**.  
  
5.  Nella finestra **Proprietà** impostare la proprietà **Label** su **Task Pane Manager**.  
  
6.  Nella scheda **Controlli barra multifunzione di Office** della **casella degli strumenti** trascinare un controllo **ToggleButton** nel gruppo **Task Pane Manager**.  
  
7.  Fare clic su **toggleButton1**.  
  
8.  Nella finestra **Proprietà** impostare la proprietà **Label** su **Mostra riquadro attività**.  
  
## Progettazione dell'interfaccia utente del riquadro attività personalizzato  
 Non sono presenti finestre di visualizzazione visiva per i riquadri attività personalizzati, ma è possibile progettare un controllo utente con il layout desiderato. Più avanti in questa procedura dettagliata il controllo utente verrà aggiunto al riquadro attività personalizzato.  
  
#### Per progettare l'interfaccia utente del riquadro attività personalizzato  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** modificare il nome del controllo utente in **TaskPaneControl**, quindi fare clic su **Aggiungi**.  
  
     Il controllo utente viene visualizzato nella finestra di progettazione.  
  
3.  Nella scheda **Controlli comuni** della **casella degli strumenti** trascinare un controllo **TextBox** nel controllo utente.  
  
## Creazione del riquadro attività personalizzato  
 Per creare il riquadro attività personalizzato quando viene avviato il componente aggiuntivo VSTO, aggiungere il controllo utente al riquadro attività nel gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> del componente aggiuntivo VSTO. Per impostazione predefinita, il riquadro attività personalizzato non è visibile. Più avanti nella procedura dettagliata verrà aggiunto il codice che consente di visualizzare o nascondere il riquadro attività quando l'utente fa clic sull'interruttore aggiunto alla barra multifunzione.  
  
#### Per creare il riquadro attività personalizzato  
  
1.  In **Esplora soluzioni**, espandere **Excel**.  
  
2.  Fare clic con il pulsante destro del mouse su **ThisAddIn.cs** o **ThisAddIn.vb**, quindi scegliere **Visualizza codice**.  
  
3.  Aggiungere il codice seguente alla classe `ThisAddIn`. Questo codice dichiara un'istanza di `TaskPaneControl` come membro di `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#1)]  
  
4.  Sostituire il gestore eventi `ThisAddIn_Startup` con il codice seguente. Questo codice aggiunge l'oggetto `TaskPaneControl` al campo `CustomTaskPanes`, ma non visualizza il riquadro attività personalizzato \(per impostazione predefinita, la proprietà <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> della classe <xref:Microsoft.Office.Tools.CustomTaskPane> è **false**\). Il codice Visual C\# collega anche un gestore eventi all'evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#2)]  
  
5.  Aggiungere il metodo seguente alla classe `ThisAddIn`. Questo metodo gestisce l'evento <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>. Quando l'utente chiude il riquadro attività facendo clic sul pulsante **Chiudi** \(X\), questo metodo aggiorna lo stato dell'interruttore nella barra multifunzione.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#3)]  
  
6.  Aggiungere la proprietà seguente alla classe `ThisAddIn`. Questa proprietà espone l'oggetto `myCustomTaskPane1` privato alle altre classi. Più avanti nella procedura dettagliata verrà aggiunto il codice alla classe `MyRibbon` che usa questa proprietà.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#4)]  
  
## Nascondere e visualizzare il riquadro attività personalizzato con l'interruttore  
 L'ultimo passaggio consiste nell'aggiungere il codice che visualizza o nasconde il riquadro attività personalizzato quando l'utente fa clic sull'interruttore nella barra multifunzione.  
  
#### Per visualizzare e nascondere il riquadro attività personalizzato con l'interruttore  
  
1.  Nella finestra di progettazione della barra multifunzione fare doppio clic sull'interruttore **Mostra riquadro attività**.  
  
     Visual Studio genera automaticamente un gestore eventi denominato `toggleButton1_Click`, che gestisce l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore. Visual Studio apre anche il file **MyRibbon.cs** o **MyRibbon.vb** nell'editor di codice.  
  
2.  Sostituire il gestore eventi `toggleButton1_Click` con il codice seguente. Quando l'utente fa clic sull'interruttore, il codice visualizza o nasconde il riquadro attività personalizzato a seconda che l'interruttore sia premuto o meno.  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ManageTaskPaneRibbon.cs#5)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ManageTaskPaneRibbon.vb#5)]  
  
## Test del componente aggiuntivo  
 Quando si esegue il progetto, Excel viene aperto senza visualizzare il riquadro attività personalizzato. Fare clic sull'interruttore nella barra multifunzione per testare il codice.  
  
#### Per testare il componente aggiuntivo VSTO  
  
1.  Premere F5 per eseguire il progetto.  
  
     Verificare che Excel si apra e che la scheda **Componenti aggiuntivi** venga visualizzata nella barra multifunzione.  
  
2.  Fare clic sulla scheda **Componenti aggiuntivi** nella barra multifunzione.  
  
3.  Nel gruppo **Task Pane Manager** fare clic sull'interruttore **Mostra riquadro attività**.  
  
     Verificare che il riquadro attività venga visualizzato e nascosto alternativamente quando si fa clic sull'interruttore.  
  
4.  Quando il riquadro attività è visibile, fare clic sul pulsante **Chiudi** \(X\) nell'angolo del riquadro attività.  
  
     Verificare che l'interruttore non sia premuto.  
  
## Passaggi successivi  
 Per altre informazioni su come creare i riquadri attività personalizzati, vedere gli argomenti seguenti:  
  
-   Creare un riquadro attività personalizzato in un componente aggiuntivo VSTO per un'applicazione diversa. Per altre informazioni sulle applicazioni che supportano i riquadri attività personalizzati, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
-   Automatizzare un'applicazione da un riquadro attività personalizzato. Per altre informazioni, vedere [Procedura dettagliata: automazione di un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).  
  
-   Creare un riquadro attività personalizzato per ogni messaggio di posta elettronica aperto in Outlook. Per altre informazioni, vedere [Procedura dettagliata: Visualizzazione dei riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## Vedere anche  
 [Riquadri attività personalizzati](../vsto/custom-task-panes.md)   
 [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procedura dettagliata: automazione di un'applicazione da un riquadro attività personalizzato](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [Procedura dettagliata: Visualizzazione dei riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)  
  
  