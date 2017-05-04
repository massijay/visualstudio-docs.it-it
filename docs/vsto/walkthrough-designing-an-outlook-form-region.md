---
title: "Procedura dettagliata: progettazione di un&#39;area del modulo di Outlook | Microsoft Docs"
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
  - "aree di modulo [sviluppo per Office in Visual Studio], creazione"
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Procedura dettagliata: progettazione di un&#39;area del modulo di Outlook
  Le aree del modulo personalizzate estendono i moduli standard o personalizzati di Microsoft Office Outlook.  In questa procedura dettagliata verrà progettata un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto.  Quest'area del modulo visualizza una mappa di ogni indirizzo elencato per il contatto, inviando le informazioni sull'indirizzo al sito Web di ricerca locale di Windows Live.  Per altre informazioni sulle aree del modulo, vedere [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un nuovo progetto di componente aggiuntivo VSTO per Outlook.  
  
-   Aggiunta di un'area del modulo al progetto di componente aggiuntivo VSTO.  
  
-   Progettazione del layout dell'area del modulo.  
  
-   Personalizzazione del comportamento dell'area del modulo.  
  
-   Test dell'area del modulo di Outlook.  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso.  La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] o [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una versione video di questo argomento, vedere [Procedura video: Creazione di un'area del modulo di Outlook](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## Creazione di un nuovo progetto di componente aggiuntivo VSTO di Outlook  
 Creare prima un progetto di componente aggiuntivo VSTO di base.  
  
#### Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di componente aggiuntivo VSTO di Outlook con il nome MapItAddIn.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.  
  
3.  Salvare il progetto in qualsiasi directory.  
  
     Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Aggiunta di un'area del modulo al progetto di componente aggiuntivo VSTO di Outlook  
 Una soluzione di componente aggiuntivo VSTO di Outlook può contenere uno o più elementi dell'area del modulo di Outlook.  Aggiungere un elemento area del modulo al progetto usando la procedura guidata **Nuova area del modulo di Outlook**.  
  
#### Per aggiungere un'area del modulo al progetto di componente aggiuntivo VSTO di Outlook  
  
1.  In **Esplora soluzioni** selezionare il progetto **MapItAddIn**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Area del modulo di Outlook**, denominare il file MapIt e quindi scegliere **Aggiungi**.  
  
     Viene avviata la procedura guidata **NuovoArea del modulo di Outlook**.  
  
4.  Nella pagina **Selezionare la modalità di creazione dell'area del modulo** selezionare **Progetta nuova area del modulo** e quindi scegliere **Avanti**.  
  
5.  Nella pagina **Selezionare il tipo di area del modulo da creare** selezionare **Separato** e quindi fare clic su **Avanti**.  
  
     Un'area del modulo *Separato* aggiunge una nuova pagina a un modulo di Outlook.  Per altre informazioni sui tipi di area del modulo, vedere [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md).  
  
6.  Nella pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione** digitare **Map It** nella casella **Nome**.  
  
     Questo nome viene visualizzato sulla barra multifunzione della finestra del controllo quando il contatto è aperto.  
  
7.  Selezionare **Controlli in modalità di composizione** e **Controlli in modalità lettura** e quindi fare clic su **Avanti**.  
  
8.  Nella pagina **Identificare le classi di messaggi per la visualizzazione dell'area del modulo** deselezionare **Messaggio posta elettronica**, selezionare **Contatto** e quindi fare clic su **Fine**.  
  
     Un file MapIt.cs o MapIt.vb viene aggiunto al progetto.  
  
## Progettazione del layout dell'area del modulo  
 Sviluppare visivamente le aree del modulo usando la *progettazione aree del modulo*.  È possibile trascinare i controlli gestiti sull'area di progettazione aree del modulo.  Usare la progettazione e la finestra **Proprietà** per modificare il layout e l'aspetto del controllo.  
  
#### Per progettare il layout dell'area del modulo  
  
1.  In **Esplora soluzioni** espandere il progetto **MapItAddIn** e quindi fare doppio clic su MapIt.cs o MapIt.vb per aprire Progettazione aree del modulo.  
  
2.  Fare clic con il pulsante destro del mouse sulla finestra di progettazione e quindi scegliere **Proprietà**.  
  
3.  Nella finestra **Proprietà** impostare **Dimensione** su 664, 469.  
  
     Ciò garantisce che l'area del modulo sia sufficiente grande per visualizzare una mappa.  
  
4.  Scegliere **Casella degli strumenti** dal menu **Visualizza**.  
  
5.  Dalla scheda **Controlli comuni** della **Casella degli strumenti** aggiungere un **WebBrowser** all'area del modulo.  
  
     **WebBrowser** visualizzerà una mappa di ogni indirizzo elencato per il contatto.  
  
## Personalizzazione del comportamento dell'area del modulo  
 Aggiungere codice ai gestori eventi dell'area del modulo per personalizzare il modo in cui un'area del modulo si comporta in fase di esecuzione.  Per questa area del modulo il codice esamina le proprietà di un elemento di Outlook e determina se visualizzare l'area del modulo Map It.  Se viene visualizzata l'area del modulo, il codice consente di passare alla ricerca locale di Windows Live e caricare una mappa di ogni indirizzo elencato nel contatto di Outlook.  
  
#### Per personalizzare il comportamento dell'area del modulo  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro su MapIt.cs o MapIt.vb e quindi scegliere **Visualizza codice**.  
  
     MapIt.cs o MapIt.vb viene aperto nell'Editor di codice.  
  
2.  Espandere l'area di codice **Factory area del modulo**.  
  
     La classe della factory area del modulo denominata `MapItFactory` viene esposta.  
  
3.  Aggiungere il codice seguente al gestore eventi `MapItFactory_FormRegionInitializing`.  Questo gestore eventi viene chiamato quando l'utente apre un contatto.  Il codice seguente determina se il contatto contiene un indirizzo.  Se il contatto non contiene un indirizzo, questo codice imposta la proprietà <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> della classe <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> su **true** e l'area del modulo non viene visualizzata.  In alternativa, il componente aggiuntivo VSTO genere l'evento <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> e visualizza l'area del modulo.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
4.  Aggiungere il codice seguente al gestore eventi <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Concatena ogni indirizzo nel contatto e crea una stringa URL.  
  
    -   Chiama il metodo <xref:System.Windows.Forms.WebBrowser.Navigate%2A> dell'oggetto <xref:System.Windows.Forms.WebBrowser> e passa la stringa URL come parametro.  
  
     Il sito Web di ricerca locale viene visualizzato nell'area del modulo Map It e presenta ogni indirizzo nel riquadro di lavoro.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#2)]  
  
## Test dell'area del modulo di Outlook  
 Quando si esegue il progetto, Visual Studio apre Outlook.  Aprire un contatto per visualizzare l'area del modulo Map It.  L'area del modulo Map It viene visualizzata nel modulo di qualsiasi contatto che contiene un indirizzo.  
  
#### Per eseguire il test dell'area del modulo Map It  
  
1.  Premere F5 per eseguire il progetto.  
  
     Viene aperto Outlook.  
  
2.  In Outlook nella scheda **Pagina iniziale** scegliere **Nuovi elementi** e quindi scegliere **Contatto**.  
  
3.  Nel modulo del contatto digitare **Ann Beebe** come nome del contatto e quindi specificare i tre indirizzi seguenti.  
  
    |Tipo di indirizzo|Indirizzo|  
    |-----------------------|---------------|  
    |**Ufficio**|4567 Main St.  Buffalo, NY|  
    |**Casa**|1234 North St.  Buffalo, NY|  
    |**Altro**|3456 Main St.  Seattle, WA|  
  
4.  Salvare e chiudere il contatto.  
  
5.  Riaprire il contatto **Ann Beebe**.  
  
6.  Nel gruppo **Mostra** della barra multifunzione dell'elemento fare clic su **Map It** per aprire l'area del modulo Map It.  
  
     Viene visualizzata l'area del modulo Map It insieme al sito Web di ricerca locale.  Gli indirizzi **Ufficio**, **Casa** e **Altro** vengono visualizzati nel riquadro di lavoro.  Nel riquadro di lavoro selezionare un indirizzo da mappare.  
  
## Passaggi successivi  
 È possibile trovare altre informazioni sulla personalizzazione dell'interfaccia utente di un'applicazione di Outlook negli argomenti seguenti:  
  
-   Per altre informazioni sulla personalizzazione della barra multifunzione di un elemento Outlook, vedere [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## Vedere anche  
 [Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Creazione di aree di modulo di Outlook](../vsto/creating-outlook-form-regions.md)   
 [Linee guida per la creazione delle aree di modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Azioni personalizzate nelle aree di modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  