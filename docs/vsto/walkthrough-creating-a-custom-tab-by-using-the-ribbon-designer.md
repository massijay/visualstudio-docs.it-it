---
title: "Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione"
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
  - "riquadri azioni [sviluppo per Office in Visual Studio], controllo dalla barra multifunzione"
  - "barra multifunzione personalizzata, schede"
  - "scheda personalizzata [sviluppo per Office in Visual Studio]"
  - "personalizzazione della barra multifunzione, schede"
  - "barra multifunzione [sviluppo per Office in Visual Studio], personalizzazione"
  - "finestra di progettazione della barra multifunzione [sviluppo per Office in Visual Studio]"
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: 68
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 67
---
# Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione
  Usando la finestra di progettazione della barra multifunzione è possibile creare una scheda personalizzata per aggiungervi e posizionarvi controlli.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   [Creazione dei riquadri azioni](#BKMK_CreateActionsPanes).  
  
-   [Creazione di una scheda personalizzata](#BKMK_CreateCustomTab).  
  
-   [Attivazione e disattivazione della visualizzazione dei riquadri azioni mediante i pulsanti della scheda personalizzata](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso.  La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Creazione di un progetto Cartella di lavoro di Excel  
 I passaggi per l'utilizzo della finestra di progettazione della barra multifunzione sono quasi identici per tutte le applicazioni Office.  In questo esempio viene usata una cartella di lavoro di Excel.  
  
#### Per creare un progetto cartella di lavoro di Excel  
  
-   Creare un progetto cartella di lavoro di Excel con il nome MyExcelRibbon.  Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro viene aperta nella finestra di progettazione di Visual Studio e il progetto **MyExcelRibbon** viene aggiunto in **Esplora soluzioni**.  
  
##  <a name="BKMK_CreateActionsPanes"></a> Creazione dei riquadri azioni  
 Aggiungere due riquadri azioni personalizzati al progetto.  Successivamente si aggiungeranno alcuni pulsanti che mostrano e nascondono questi riquadri azioni alla scheda personalizzata.  
  
#### Per creare i riquadri azioni  
  
1.  Scegliere **Aggiungi nuovo elemento**dal menu **Progetto**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **ActionsPaneControl**, quindi scegliere **Aggiungi**.  
  
     Nella finestra di progettazione viene aperto il file **ActionsPaneControl1.cs** o **ActionsPaneControl1.vb**.  
  
3.  Dalla scheda **Controlli comuni** della **Casella degli strumenti** aggiungere un'etichetta all'area di progettazione.  
  
4.  Nella finestra **Proprietà** impostare la proprietà **Text** di label1 su Actions Pane 1.  
  
5.  Ripetere i passaggi da 1 a 5 per creare un secondo riquadro azioni e una seconda etichetta.  Impostare la proprietà **Text** della seconda etichetta su Actions Pane 2.  
  
##  <a name="BKMK_CreateCustomTab"></a> Creazione di una scheda personalizzata  
 Per la progettazione di applicazioni Office, è necessario che gli utenti abbiano sempre il controllo dell'interfaccia utente dell'applicazione Office.  Per aggiungere questa funzionalità relativa ai riquadri azioni, è possibile aggiungere pulsanti che mostrano e nascondono ciascun riquadro azioni da una scheda personalizzata della barra multifunzione.  Per creare una scheda personalizzata, aggiungere un elemento **Barra multifunzione \(finestra di progettazione visiva\)** al progetto.  La finestra di progettazione consente di aggiungere e posizionare controlli, impostarne le proprietà e gestirne gli eventi.  
  
#### Per creare una scheda personalizzata  
  
1.  Scegliere **Aggiungi nuovo elemento**dal menu **Progetto**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione \(finestra di progettazione visiva\)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **MyRibbon**, quindi scegliere **Aggiungi**.  
  
     Nella finestra di progettazione della barra multifunzione viene aperto un file **MyRibbon.cs** o **MyRibbon.vb**, che visualizza una scheda e un gruppo predefiniti.  
  
4.  Nella finestra di progettazione della barra multifunzione scegliere la scheda predefinita.  
  
5.  Nella finestra **Proprietà** espandere la proprietà **ControlId**, quindi impostare la proprietà **ControlIdType** su **Custom**.  
  
6.  Impostare la proprietà **Label** su My Custom Tab.  
  
7.  Nella finestra di progettazione della barra multifunzione scegliere **group1**.  
  
8.  Nella finestra **Proprietà** impostare **Etichetta** su Actions Pane Manager.  
  
9. Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare un pulsante in **group1**.  
  
10. Selezionare **button1**.  
  
11. Nella finestra **Proprietà** impostare **Etichetta** su Show Actions Pane 1.  
  
12. Aggiungere un secondo pulsante a **group1**, quindi impostare la proprietà **Label** su Show Actions Pane 2.  
  
13. Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare un controllo **ToggleButton** in **group1**.  
  
14. Impostare la proprietà **Label** su Hide Actions Pane.  
  
##  <a name="BKMK_HideShowActionsPane"></a> Attivazione e disattivazione della visualizzazione dei riquadri azioni mediante i pulsanti della scheda personalizzata  
 L'ultimo passaggio consiste nell'aggiungere codice che risponde all'utente.  Aggiungere gestori eventi per gli eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dei due pulsanti e per l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore.  Aggiungere codice a questi gestori eventi per abilitare e disabilitare la visualizzazione dei riquadri azioni.  
  
#### Per nascondere e mostrare i riquadri azioni mediante i pulsanti della scheda personalizzata  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per MyRibbon.cs o MyRibbon.vb, quindi scegliere **Visualizza codice**.  
  
2.  Aggiungere il codice riportato di seguito all'inizio della classe `MyRibbon`.  Mediante questo codice vengono creati due oggetti riquadro azioni.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#1)]  
  
3.  Sostituire il metodo `MyRibbon_Load` con il codice seguente.  Mediante questo codice vengono aggiunti alla raccolta <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> oggetti riquadro azioni, che vengono nascosti.  Il codice Visual C\# associa inoltre delegati a vari eventi del controllo della barra multifunzione.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#2)]  
  
4.  Aggiungere i tre metodi per la gestione eventi riportati di seguito alla classe `MyRibbon`.  Questi metodi gestiscono gli eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dei due pulsanti e l'evento <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> dell'interruttore.  I gestori eventi per button1 e button2 mostrano riquadri azioni alternativi.  Il gestore eventi per toggleButton1 mostra e nasconde il riquadro azioni attivo.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/CS/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab/VB/MyRibbon.vb#3)]  
  
## Verifica della scheda personalizzata  
 Quando si esegue il progetto, viene avviato Excel e sulla barra multifunzione viene visualizzata la scheda **My Custom Tab**.  Scegliere i pulsanti di **My Custom Tab** per mostrare e nascondere i riquadri azioni.  
  
#### Per verificare la scheda personalizzata  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Scegliere la scheda **My Custom Tab**.  
  
3.  Nel gruppo **Custom Actions Pane Manager** scegliere **Show Actions Pane 1**.  
  
     Viene visualizzato il riquadro azioni con l'etichetta Actions Pane 1.  
  
4.  Scegliere **Show Actions Pane 2**.  
  
     Viene visualizzato il riquadro azioni con l'etichetta Actions Pane 2.  
  
5.  Scegliere **Hide Actions Pane**.  
  
     I riquadri azioni non sono più visibili.  
  
## Passaggi successivi  
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:  
  
-   Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento.  Per altre informazioni, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md).  
  
-   Estensione di un modulo standard o personalizzato di Microsoft Office Outlook.  Per altre informazioni, vedere [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## Vedere anche  
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)  
  
  