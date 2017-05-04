---
title: "Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Web part [sviluppo per SharePoint in Visual Studio], creazione"
  - "Web part [sviluppo per SharePoint in Visual Studio], finestra di progettazione"
  - "Web part [sviluppo per SharePoint in Visual Studio], progettazione"
ms.assetid: 3dd62654-ada2-468f-b7da-eb5704a2ff7a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione
  Se si creano web part per un sito SharePoint, gli utenti possono modificare direttamente il contenuto, l'aspetto e il comportamento delle pagine in tale sito utilizzando un browser.  In questa procedura dettagliata viene illustrato come creare visivamente una web part tramite il modello di progetto **Web part visiva** di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Nella web part creata viene riprodotta una visualizzazione del calendario mensile e una casella di controllo per ogni elenco di calendario presente nel sito.  Gli utenti possono specificare quali elenchi di calendario includere nella visualizzazione del calendario mensile selezionando le caselle di controllo.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di una Web part tramite il modello di progetto **Web part visiva**.  
  
-   Progettazione della web part tramite la finestra di progettazione di Visual Web Developer in Visual Studio.  
  
-   Aggiunta di codice per gestire gli eventi dei controlli nella Web part.  
  
-   Test della web part in SharePoint.  
  
    > [!NOTE]  
    >  Nel computer potrebbero essere visualizzati nomi o percorsi differenti per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Windows e SharePoint.  Vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] o superiore.  
  
## Creazione di un progetto Web part  
 Creare innanzitutto un progetto web part tramite il modello di progetto **Web part visiva**.  
  
#### Per creare una progetto Web part visiva  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizzando l'opzione **Esegui come amministratore**.  
  
2.  Nella barra dei menu, scegliere **File**, **Nuovo**, **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
3.  Nella finestra di dialogo **Nuovo progetto**, in **Visual C\#** o **Visual Basic** espandere **Office\/SharePoint** e quindi selezionare la categoria **Soluzioni SharePoint**.  
  
4.  Nell'elenco di modelli, scegliere il modello **SharePoint 2013 \- Web part visiva** e quindi scegliere il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  Utilizzando questa procedura guidata, è possibile specificare il sito che verrà utilizzato per eseguire il debug del progetto e il livello di attendibilità della soluzione.  
  
5.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm**.  
  
6.  Selezionare il pulsante **Fine** per accettare il sito SharePoint locale predefinito.  
  
## Progettazione della web part  
 Progettare la web part aggiungendo i controlli dalla **Casella degli strumenti** all'area della finestra di progettazione di Visual Web Developer.  
  
#### Per progettare il layout della web part  
  
1.  Nella finestra di progettazione di Visual Web Developer, scegliere la scheda **Progettazione** per passare alla visualizzazione di progettazione.  
  
2.  Nella barra dei menu, scegliere **Visualizza**, **Casella degli strumenti**.  
  
3.  Nel nodo **Standard** della **Casella degli strumenti** scegliere il controllo **CheckBoxList** e quindi eseguire una delle operazioni seguenti:  
  
    -   Aprire il menu di scelta rapida per il controllo **CheckBoxList**, scegliere **Copia**, aprire il menu di scelta rapida per la prima riga nella finestra di progettazione e quindi scegliere **Incolla**.  
  
    -   Trascinare il controllo **CheckBoxList** da **Casella degli strumenti** e connettere il controllo alla prima riga nella finestra di progettazione.  
  
4.  Ripetere il passaggio precedente, ma spostare un pulsante alla riga successiva della finestra di progettazione.  
  
5.  Nella finestra di progettazione, fare doppio clic sul pulsante **Button1**.  
  
6.  Nella barra dei menu, scegliere **Visualizza**, **Finestra proprietà**.  
  
     Viene aperta la finestra **Proprietà**.  
  
7.  Nella proprietà **Testo** del pulsante immettere update.  
  
## Gestione degli eventi dei controlli nella web part  
 Aggiungere codice che consenta all'utente di includere calendari alla visualizzazione del calendario master.  
  
#### Per gestire gli eventi dei controlli nella web part  
  
1.  Eseguire una delle procedure seguenti:  
  
    -   Nella finestra di progettazione fare doppio clic sul pulsante **Aggiorna**.  
  
    -   Nella finestra **Proprietà** per il pulsante **Aggiorna** scegliere il pulsante **Eventi**.  Nella proprietà **Click** immettere **Button1\_Click**, quindi scegliere il tasto Invio.  
  
     Il file di codice del controllo utente verrà aperto nell'editor di codice e verrà visualizzato il gestore eventi `Button1_Click`.  In un secondo momento, si aggiungerà codice a questo gestore eventi.  
  
2.  Aggiungere le seguenti istruzioni all'inizio del file di codice del controllo utente.  
  
     [!code-csharp[SP_VisualWebPart#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]
     [!code-vb[SP_VisualWebPart#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]  
  
3.  Aggiungere la riga di codice seguente alla classe `VisualWebPart1`.  Questo codice dichiara un controllo della visualizzazione del calendario mensile.  
  
     [!code-csharp[SP_VisualWebPart#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]
     [!code-vb[SP_VisualWebPart#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]  
  
4.  Sostituire il metodo `Page_Load` della classe `VisualWebPart1` con il codice riportato di seguito.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Aggiunge una visualizzazione del calendario mensile al controllo utente.  
  
    -   Aggiunge una casella di controllo per ogni elenco di calendario sul sito.  
  
    -   Specifica un modello per ogni tipo di elemento presente nella visualizzazione del calendario.  
  
     [!code-csharp[SP_VisualWebPart#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]
     [!code-vb[SP_VisualWebPart#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]  
  
5.  Sostituire il metodo `Button1_Click` della classe `VisualWebPart1` con il codice riportato di seguito.  Questo codice aggiunge elementi da ogni calendario selezionato alla visualizzazione del calendario master.  
  
     [!code-csharp[SP_VisualWebPart#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_visualwebpart/cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]
     [!code-vb[SP_VisualWebPart#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_visualwebpart/vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]  
  
## Test della web part  
 Quando si esegue il progetto viene aperto il sito di SharePoint.  La web part viene aggiunta automaticamente alla Raccolta web part in SharePoint.  Per eseguire il test di questo progetto, dovranno essere completate le attività seguenti:  
  
-   Aggiungere un evento a ognuno di due elenchi di calendario distinti.  
  
-   Aggiungere la Web part a una pagina della Web part.  
  
-   Specificare gli elenchi da includere nella visualizzazione del calendario mensile.  
  
#### Per aggiungere eventi agli elenchi di calendario sul sito  
  
1.  In Visual Studio, selezionare il pulsante F5.  
  
     Viene aperto il sito di SharePoint e la barra Avvio veloce di [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] viene visualizzata nella pagina.  
  
2.  Sulla barra di Avvio veloce, in **Elenchi** scegliere il collegamento **Calendario**.  
  
     Verrà visualizzata la pagina **Calendario**.  
  
     Se non viene visualizzato alcun collegamento del calendario nella barra avvio veloce, scegliere il collegamento **Contenuto del sito**.  Se nella pagina Contenuti del sito non viene visualizzato un elemento **Calendario**, crearne uno.  
  
3.  Nella pagina del Calendario, scegliere un giorno e quindi scegliere il collegamento **Aggiungi** nel giorno selezionato per aggiungere un evento.  
  
4.  Nella casella **Titolo** immettere Evento nel calendario predefinito, quindi scegliere il pulsante **Salva**.  
  
5.  Selezionare il collegamento **Sito indice**, quindi selezionare la sezione **Aggiungi app**.  
  
6.  Nella pagina **Crea** scegliere il tipo **Calendario**, assegnare un nome al calendario, quindi scegliere il pulsante **Crea**.  
  
7.  Aggiungere un evento al nuovo calendario, denominare l'evento Event in the custom calendar, quindi scegliere **Salva**.  
  
#### Per aggiungere la web part a una pagina di web part  
  
1.  Nella pagina **Contenuto del sito** aprire la cartella **Pagine sito**.  
  
2.  Sulla barra multifunzione, scegliere la scheda **File**, aprire il menu **Nuovo documento** e quindi scegliere il comando **Pagina Web part**.  
  
3.  Nella pagina **Nuova pagina web part**, denominare la pagina **SampleWebPartPage.aspx**, quindi scegliere il pulsante **Crea**.  
  
     Viene visualizzata la pagina web part.  
  
4.  Nella parte superiore della pagina Web part scegliere la scheda **Inserisci** e quindi fare clic sul pulsante **Web part**.  
  
5.  Selezionare la cartella **Personalizzata**, selezionare la web part **VisualWebPart1**, quindi selezionare il pulsante **Aggiungi**.  
  
     La web part viene visualizzata nella pagina.  I controlli seguenti vengono visualizzati nella web part:  
  
    -   Una visualizzazione del calendario mensile.  
  
    -   Un pulsante **Aggiorna**.  
  
    -   Una casella di controllo **Calendario**.  
  
    -   Casella di controllo **Calendario personalizzato**.  
  
#### Per specificare gli elenchi da includere nella visualizzazione del calendario mensile  
  
1.  Nella Web part specificare i calendari che si desidera includere nella visualizzazione del calendario mensile, quindi scegliere il pulsante **Aggiorna**.  
  
     Gli eventi di tutti i calendari specificati vengono visualizzati nella visualizzazione del calendario mensile.  
  
## Vedere anche  
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Procedura: creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procedura dettagliata: creazione di una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  