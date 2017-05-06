---
title: "Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione"
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
  - "controlli [sviluppo per Office in Visual Studio], barra multifunzione"
  - "menu dinamici [sviluppo per Office in Visual Studio]"
  - "barra multifunzione [sviluppo per Office in Visual Studio], controlli"
  - "barra multifunzione [sviluppo per Office in Visual Studio], menu dinamico"
  - "barra multifunzione [sviluppo per Office in Visual Studio], aggiornamento"
  - "aggiornamento dei controlli della barra multifunzione"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione
  Questa procedura dettagliata illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli di una barra multifunzione dopo che la barra multifunzione è stata caricata nell'applicazione Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 L'esempio usa i dati del database di esempio Northwind per popolare una casella combinata e un menu in Microsoft Office Outlook.  Gli elementi che si selezionano in questi controlli popolano automaticamente campi quali **A** e **Oggetto** in un messaggio di posta elettronica.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un nuovo progetto di componente aggiuntivo VSTO per Outlook.  
  
-   Progettazione di un gruppo personalizzato della barra multifunzione.  
  
-   Aggiunta del gruppo personalizzato a una scheda predefinita.  
  
-   Aggiornamento dei controlli della barra multifunzione in fase di esecuzione.  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso.  La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Creazione di un nuovo progetto di componente aggiuntivo VSTO di Outlook  
 Prima di tutto, creare un progetto di componente aggiuntivo VSTO di Outlook.  
  
#### Per creare un nuovo progetto di componente aggiuntivo VSTO di Outlook  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di componente aggiuntivo VSTO di Outlook con il nome Ribbon\_Update\_At\_Runtime.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Crea directory per soluzione**.  
  
3.  Salvare il progetto nella directory del progetto predefinita.  
  
     Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Progettazione di un gruppo personalizzato della barra multifunzione  
 La barra multifunzione per questo esempio verrà visualizzata quando un utente compone un nuovo messaggio di posta.  Per creare un gruppo personalizzato per la barra multifunzione, aggiungere prima un elemento barra multifunzione al progetto, quindi progettare il gruppo nella finestra di progettazione della barra multifunzione.  Questo gruppo personalizzato consente di generare messaggi di posta elettronica da completare per i clienti usando nomi e cronologie di ordine di un database.  
  
#### Per progettare un gruppo personalizzato  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione \(finestra di progettazione visiva\)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **CustomerRibbon**, quindi fare clic su **Aggiungi**.  
  
     Nella finestra di progettazione della barra multifunzione viene aperto un file **CustomerRibbon.cs** o **CustomerRibbon.vb**, che visualizza una scheda e un gruppo predefiniti.  
  
4.  Fare clic nella finestra di progettazione per selezionarlo.  
  
5.  Nella finestra **Proprietà** fare clic sulla freccia a discesa accanto alla proprietà **RibbonType** e selezionare **Microsoft.Outlook.Mail.Compose**.  
  
     In tal modo, la barra multifunzione viene visualizzata quando l'utente compone un nuovo messaggio di posta in Outlook.  
  
6.  Nella finestra di progettazione della barra multifunzione fare clic su **Group1** per selezionarlo.  
  
7.  Nella finestra **Proprietà** impostare **Etichetta** su Customer Purchases.  
  
8.  Dalla scheda **Controlli barra multifunzione** di Office della **Casella degli strumenti**, trascinare una **casella combinata** sul gruppo **Customer Purchases**.  
  
9. Fare clic su **ComboBox1** per selezionarlo.  
  
10. Nella finestra **Proprietà** impostare **Etichetta** su Customers.  
  
11. Dalla scheda **Controlli barra multifunzione** di Office della **Casella degli strumenti**, trascinare un **Menu** sul gruppo **Customer Purchases**.  
  
12. Nella finestra **Proprietà** impostare **Etichetta** su Product Purchased.  
  
13. Impostare **Dinamico** su **true**.  
  
     In tal modo, è possibile aggiungere e rimuovere i controlli nel menu in fase di esecuzione dopo che la barra multifunzione è stata caricata nell'applicazione Office.  
  
## Aggiunta del gruppo personalizzato a una scheda predefinita  
 Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di una finestra di esplorazione o di un controllo di Outlook.  In questa procedura, si aggiunge il gruppo personalizzato a una scheda predefinita e quindi si specifica la posizione del gruppo personalizzato nella scheda.  
  
#### Per aggiungere il gruppo personalizzato a una scheda predefinita  
  
1.  Fare clic sulla scheda **TabAddins \(Built\-In\)** per selezionarla.  
  
2.  Nella finestra **Proprietà** espandere la proprietà **ControlId**, quindi impostare **OfficeId** su TabNewMailMessage.  
  
     Il gruppo **Customer Purchases** viene così aggiunto alla scheda **Messaggi** della barra multifunzione che viene visualizzata in un nuovo messaggio di posta.  
  
3.  Fare clic sul gruppo **Customer Purchases** per selezionarlo.  
  
4.  Nella finestra **Proprietà**, espandere la proprietà **Posizione**, fare clic sulla freccia a discesa accanto alla proprietà **PositionType**, quindi fare clic su **BeforeOfficeId**.  
  
5.  Impostare la proprietà **OfficeId** su GroupClipboard.  
  
     Il gruppo **Customer Purchases** viene così posizionato prima del gruppo **Appunti** della scheda **Messaggi**.  
  
## Creazione dell'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Verrà avviata la **Configurazione guidata origine dati**.  
  
2.  Selezionare **Database**, quindi scegliere **Avanti**.  
  
3.  Selezionare **Dataset**, quindi scegliere **Avanti**.  
  
4.  Selezionare una connessione dati al database di esempio Northwind di Microsoft SQL Server Compact 4.0 oppure aggiungere una nuova connessione con il pulsante **Nuova connessione**.  
  
5.  Dopo aver selezionato o creato una connessione, scegliere **Avanti**.  
  
6.  Fare clic su **Avanti** per salvare la stringa di connessione.  
  
7.  Nella pagina **Seleziona oggetti di database** espandere **Tabelle**.  
  
8.  Selezionare la casella di controllo accanto a ciascuna delle seguenti tabelle:  
  
    1.  **Clienti**  
  
    2.  **Order Details**  
  
    3.  **Orders**  
  
    4.  **Prodotti**  
  
9. Scegliere **Fine**.  
  
## Aggiornamento dei controlli nel gruppo personalizzato in fase di esecuzione  
 Usare il modello a oggetti della barra multifunzione per effettuare le seguenti attività:  
  
-   Aggiungere nomi di clienti nella casella combinata **Customers**.  
  
-   Aggiungere menu e controlli di pulsanti al menu **Products Purchased** che rappresenta gli ordini di vendita e i prodotti venduti.  
  
-   Popolare i campi To, Subject e Body dei nuovi messaggi di posta usando i dati della casella combinata **Customers** e del menu **Products Purchased**.  
  
#### Per aggiornare i controlli nel gruppo personalizzato usando il modello a oggetti della barra multifunzione  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi riferimento**.  
  
2.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **.NET**, selezionare l'assembly **System.Data.Linq**, quindi scegliere **OK**.  
  
     Questo assembly contiene le classi per l'uso di Language\-Integrated Queries \(LINQ\).  LINQ viene usato per popolare i controlli nel gruppo personalizzato con i dati del database Northwind.  
  
3.  In **Esplora soluzioni** fare clic su **CustomerRibbon.cs** o **CustomerRibbon.vb** per selezionarlo.  
  
4.  Scegliere **Codice** dal menu **Visualizza**.  
  
     Il file di codice della barra multifunzione viene aperto nell'editor di codice.  
  
5.  Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione.  Queste istruzioni forniscono l'accesso agli spazi dei nomi LINQ e allo spazio dei nomi dell'assembly di interoperabilità primario \(PIA\) di Outlook.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  Aggiungere il codice seguente all'interno della classe CustomerRibbon.  Il codice dichiara la tabella dati e gli adattatori di tabella che verranno usati per archiviare le informazioni delle tabelle Clienti, Ordini, Dettagli sugli ordini e Prodotti del database Northwind.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  Aggiungere il seguente blocco di codice alla classe `CustomerRibbon`.  Questo codice aggiunge tre metodi di supporto che creano i controlli per la barra multifunzione in fase di esecuzione.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  Sostituire il metodo del gestore eventi `CustomerRibbon_Load` con il codice seguente.  Questo codice usa una query LINQ per eseguire le attività seguenti:  
  
    -   Popolare la casella combinata **Customers** usando l'ID e il nome di 20 clienti del database Northwind.  
  
    -   Chiama il metodo di supporto `PopulateSalesOrderInfo`.  Questo metodo aggiorna il menu **Products Purchased** con i numeri degli ordini di vendita relativi al cliente attualmente selezionato.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. Aggiungere il codice seguente alla classe `CustomerRibbon`.  Questo codice usa le query LINQ per eseguire le attività seguenti:  
  
    -   Aggiungere un sottomenu al menu **Products Purchased** per ogni ordine di vendita relativo al cliente selezionato.  
  
    -   Aggiungere pulsanti a ogni sottomenu per i prodotti relativi all'ordine di vendita.  
  
    -   Aggiungere gestori eventi a ogni pulsante.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. In **Esplora soluzioni** fare doppio clic sul file di codice della barra multifunzione.  
  
     La finestra di progettazione della barra multifunzione viene aperta.  
  
11. Nella finestra di progettazione della barra multifunzione, fare doppio clic sulla casella di controllo **Customers**.  
  
     Nell'editor di codice viene aperto il file di codice della barra multifunzione e viene visualizzato il gestore eventi `ComboBox1_TextChanged`.  
  
12. Sostituire il gestore eventi `ComboBox1_TextChanged` con il codice seguente.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Chiama il metodo di supporto `PopulateSalesOrderInfo`.  Questo metodo aggiorna il menu **Products Purchased** con gli ordini di vendita relativi al cliente selezionato.  
  
    -   Chiama il metodo di supporto `PopulateMailItem` e passa al testo corrente, ossia il nome del cliente selezionato.  Questo metodo popola i campi To, Subject e Body dei nuovi messaggi di posta.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. Aggiungere il gestore dell'evento Click indicato di seguito alla classe `CustomerRibbon`.  Questo codice aggiunge il nome dei prodotti selezionati nel campo Body dei nuovi messaggi di posta.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. Aggiungere il codice seguente alla classe `CustomerRibbon`.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Inserisce la riga To dei nuovi messaggi di posta usando l'indirizzo di posta elettronica del cliente attualmente selezionato.  
  
    -   Aggiunge il testo nei campi Subject e Body dei nuovi messaggi di posta.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## Test dei controlli nel gruppo personalizzato  
 Quando si apre un nuovo modulo di posta in Outlook, un gruppo personalizzato denominato **Customer Purchases** viene visualizzato nella scheda **Messaggi** della barra multifunzione.  
  
 Per creare un messaggio di posta elettronica da completare per il cliente, selezionare un cliente e quindi selezionare i prodotti acquistati dal cliente.  I controlli nel gruppo **Customer Purchases** vengono aggiornati in fase di esecuzione con i dati del database Northwind.  
  
#### Per testare i controlli nel gruppo personalizzato  
  
1.  Premere F5 per eseguire il progetto.  
  
     Viene avviato Outlook.  
  
2.  In Outlook scegliere **Nuovo** dal menu **File**, quindi fare clic su **Messaggio di posta**.  
  
     Si verificano le seguenti azioni:  
  
    -   Viene visualizzata una nuova finestra di controllo del messaggio di posta.  
  
    -   Il gruppo **Customer Purchases** viene posizionato prima del gruppo **Appunti** della scheda **Messaggio** della barra multifunzione.  
  
    -   La casella combinata **Customers** nel gruppo viene aggiornata con i nomi dei clienti del database Northwind.  
  
3.  Nella scheda **Messaggio** della barra multifunzione, nel gruppo **Customer Purchases**, selezionare un cliente dalla casella combinata **Customers**.  
  
     Si verificano le seguenti azioni:  
  
    -   Il menu **Products Purchased** viene aggiornato in modo da visualizzare ogni ordine di vendita per il cliente selezionato.  
  
    -   Ogni sottomenu dell'ordine di vendita viene aggiornato in modo da visualizzare i prodotti acquistati in quell'ordine.  
  
    -   L'indirizzo di posta elettronica del cliente selezionato viene aggiunto nella riga **A** del messaggio di posta e l'oggetto e il corpo del messaggio di posta vengono popolati con un testo.  
  
4.  Fare clic sul menu **Products Purchased**, selezionare un ordine di vendita e quindi fare clic su un prodotto dall'ordine di vendita.  
  
     Il nome di prodotto viene aggiunto al corpo del messaggio di posta.  
  
## Passaggi successivi  
 È possibile trovare ulteriori informazioni sulla personalizzazione dell'interfaccia utente di Office nei seguenti argomenti:  
  
-   Aggiunta di un'interfaccia utente basata sul contesto a una personalizzazione a livello di documento.  Per altre informazioni, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md).  
  
-   Estensione di un modulo standard o personalizzato di Microsoft Office Outlook.  Per altre informazioni, vedere [Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Aggiungere un riquadro attività personalizzato a Outlook.  Per altre informazioni, vedere [Riquadri attività personalizzati](../vsto/custom-task-panes.md).  
  
## Vedere anche  
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [LINQ \(Language\-Integrated Query\)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  