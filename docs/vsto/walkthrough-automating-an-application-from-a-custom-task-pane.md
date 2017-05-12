---
title: "Procedura dettagliata: automazione di un&#39;applicazione da un riquadro attivit&#224; personalizzato"
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
  - "riquadri attività [sviluppo per Office in Visual Studio], PowerPoint"
  - "PowerPoint [sviluppo per Office in Visual Studio], riquadri attività personalizzati"
  - "automazione delle applicazioni di Office"
  - "riquadri attività personalizzati [sviluppo per Office in Visual Studio], automazione delle applicazioni"
  - "riquadri attività personalizzati [sviluppo per Office in Visual Studio], PowerPoint"
  - "riquadri attività [sviluppo per Office in Visual Studio], automazione delle applicazioni"
ms.assetid: 77be5ab5-e330-4564-87ec-9cba564ba8f9
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura dettagliata: automazione di un&#39;applicazione da un riquadro attivit&#224; personalizzato
  Questa procedura dettagliata mostra come creare un riquadro attività personalizzato che consente di automatizzare PowerPoint. Il riquadro attività personalizzato inserisce le date in una diapositiva quando l'utente fa clic su un controllo <xref:System.Windows.Forms.MonthCalendar> che si trova nel riquadro attività personalizzato.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Benché questa procedura dettagliata usi PowerPoint in modo specifico, i concetti illustrati sono applicabili a tutte le applicazioni elencate in precedenza.  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Progettazione dell'interfaccia utente del riquadro attività personalizzato.  
  
-   Automazione di PowerPoint dal riquadro attività personalizzato.  
  
-   Visualizzazione del riquadro attività personalizzato in PowerPoint.  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 o [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## Creazione del progetto di componente aggiuntivo  
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per PowerPoint.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto di componente aggiuntivo VSTO per PowerPoint denominato **MyAddIn**, usando il modello per il progetto di componente aggiuntivo di PowerPoint. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il file di codice **ThisAddIn.cs** o **ThisAddIn.vb** e aggiunge il progetto **MyAddIn** a **Esplora soluzioni**.  
  
## Progettazione dell'interfaccia utente del riquadro attività personalizzato  
 Non sono presenti finestre di visualizzazione visiva per i riquadri attività personalizzati, ma è possibile progettare un controllo utente con il layout desiderato. Più avanti in questa procedura dettagliata il controllo utente verrà aggiunto al riquadro attività personalizzato.  
  
#### Per progettare l'interfaccia utente del riquadro attività personalizzato  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi controllo utente**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** modificare il nome del controllo utente su **MyUserControl** e fare clic su **Aggiungi**.  
  
     Il controllo utente viene visualizzato nella finestra di progettazione.  
  
3.  Nella scheda **Controlli comuni** della **casella degli strumenti** trascinare un controllo **MonthCalendar** nel controllo utente.  
  
     Se il controllo **MonthCalendar** è più ampio dell'area di progettazione del controllo utente, ridimensionare il controllo utente per adattare il controllo **MonthCalendar**.  
  
## Automazione di PowerPoint dal riquadro attività personalizzato  
 Lo scopo del componente aggiuntivo VSTO è inserire una data selezionata nella prima diapositiva della presentazione attiva. Usare l'evento <xref:System.Windows.Forms.MonthCalendar.DateChanged> del controllo per aggiungere la data selezionata ogni volta che viene modificata.  
  
#### Per automatizzare PowerPoint dal riquadro attività personalizzato  
  
1.  Nella finestra di progettazione fare doppio clic sul controllo <xref:System.Windows.Forms.MonthCalendar>.  
  
     Il file **MyUserControl.cs** o **MyUserControl.vb** si apre e viene creato un gestore eventi per l'evento <xref:System.Windows.Forms.MonthCalendar.DateChanged>.  
  
2.  Aggiungere il codice seguente all'inizio del file. Questo codice crea gli alias per gli spazi dei nomi <xref:Microsoft.Office.Core> e <xref:Microsoft.Office.Interop.PowerPoint>.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#1)]  
  
3.  Aggiungere il codice seguente alla classe `MyUserControl`. Questo codice dichiara un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Shape> come membro di `MyUserControl`. Nel passaggio seguente viene usato <xref:Microsoft.Office.Interop.PowerPoint.Shape> per aggiungere una casella di testo a una diapositiva nella presentazione attiva.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#2)]  
  
4.  Sostituire il gestore eventi `monthCalendar1_DateChanged` con il codice seguente. Questo codice aggiunge una casella di testo alla prima diapositiva nella presentazione attiva, quindi aggiunge la data attualmente selezionata alla casella di testo. Questo codice usa l'oggetto `Globals.ThisAddIn` per accedere al modello di oggetto di PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#3)]  
  
5.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto **MyAddIn**, quindi scegliere **Compila**. Verificare che il progetto venga compilato senza errori.  
  
## Visualizzazione del riquadro attività personalizzato  
 Per visualizzare il riquadro attività personalizzato quando viene avviato il componente aggiuntivo VSTO, aggiungere il controllo utente al riquadro attività nel gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> del componente aggiuntivo VSTO.  
  
#### Per visualizzare il riquadro attività personalizzato  
  
1.  In **Esplora soluzioni** espandere **PowerPoint**.  
  
2.  Fare clic con il pulsante destro del mouse su **ThisAddIn.cs** o **ThisAddIn.vb**, quindi scegliere **Visualizza codice**.  
  
3.  Aggiungere il codice seguente alla classe `ThisAddIn`. Questo codice dichiara le istanze di `MyUserControl` e <xref:Microsoft.Office.Tools.CustomTaskPane> come membri della classe `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#4)]  
  
4.  Sostituire il gestore eventi `ThisAddIn_Startup` con il codice seguente. Questo codice crea un nuovo oggetto <xref:Microsoft.Office.Tools.CustomTaskPane> aggiungendo l'oggetto `MyUserControl` alla raccolta `CustomTaskPanes`. Il codice visualizza anche il riquadro attività.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#5)]  
  
## Test del componente aggiuntivo  
 Quando si esegue il progetto, PowerPoint si apre e il componente aggiuntivo VSTO visualizza il riquadro attività personalizzato. Fare clic sul controllo <xref:System.Windows.Forms.MonthCalendar> per testare il codice.  
  
#### Per testare il componente aggiuntivo VSTO  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro attività personalizzato sia visibile.  
  
3.  Fare clic su una data nel controllo <xref:System.Windows.Forms.MonthCalendar> nel riquadro attività.  
  
     La data viene inserita nella prima diapositiva della presentazione attiva.  
  
## Passaggi successivi  
 Per altre informazioni su come creare i riquadri attività personalizzati, vedere gli argomenti seguenti:  
  
-   Creare un riquadro attività personalizzato in un componente aggiuntivo VSTO per un'applicazione diversa. Per altre informazioni sulle applicazioni che supportano i riquadri attività personalizzati, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
-   Creare un pulsante della barra multifunzione da usare per visualizzare o nascondere un riquadro attività personalizzato. Per altre informazioni, vedere [Procedura dettagliata: Sincronizzazione di un riquadro attività personalizzato con una barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Creare un riquadro attività personalizzato per ogni messaggio di posta elettronica aperto in Outlook. Per altre informazioni, vedere [Procedura dettagliata: Visualizzazione dei riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## Vedere anche  
 [Riquadri attività personalizzati](../vsto/custom-task-panes.md)   
 [Procedura: aggiungere un riquadro attività personalizzato a un'applicazione](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Procedura dettagliata: Sincronizzazione di un riquadro attività personalizzato con una barra multifunzione](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Procedura dettagliata: Visualizzazione dei riquadri attività personalizzati con messaggi di posta elettronica in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  