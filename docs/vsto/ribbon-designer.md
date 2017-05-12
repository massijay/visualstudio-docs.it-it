---
title: "Finestra di progettazione della barra multifunzione"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controlli [sviluppo per Office in Visual Studio], barra multifunzione"
  - "barra multifunzione personalizzata"
  - "barra multifunzione personalizzata, informazioni sulla finestra di progettazione della barra multifunzione"
  - "personalizzazione della barra multifunzione"
  - "personalizzazione della barra multifunzione, informazioni sulla finestra di progettazione della barra multifunzione"
  - "finestre di progettazione [sviluppo per Office in Visual Studio], barra multifunzione"
  - "proprietà di sola lettura"
  - "barra multifunzione [sviluppo per Office in Visual Studio], attività comuni"
  - "barra multifunzione [sviluppo per Office in Visual Studio], controlli"
  - "barra multifunzione [sviluppo per Office in Visual Studio], personalizzazione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], tasti di scelta rapida"
  - "barra multifunzione [sviluppo per Office in Visual Studio], finestra di progettazione di Visual"
  - "finestra di progettazione della barra multifunzione [sviluppo per Office in Visual Studio]"
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# Finestra di progettazione della barra multifunzione
  La finestra di progettazione della barra multifunzione rappresenta un'area di progettazione visiva.  È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'applicazione di Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Per aprire tale finestra di progettazione, aggiungere un elemento **Barra multifunzione \(finestra di progettazione visiva\)** al progetto.  È possibile quindi utilizzare gli strumenti di progettazione per l'esecuzione delle seguenti attività:  
  
-   [Progettazione del layout della barra multifunzione](#DesigningRibbonLayout)  
  
-   [Gestione degli eventi e impostazione delle proprietà dei controlli](#HandleEventsSetProperties)  
  
-   [Aggiungere i controlli alla visualizzazione Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Alcune attività, tuttavia, non possono essere eseguite utilizzando la finestra di progettazione della barra multifunzione.  Per ulteriori informazioni su queste attività e sulle possibili modalità di esecuzione, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere la procedura relativa all' [utilizzo della finestra di progettazione per personalizzare la barra multifunzione in Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## Aggiunta di un elemento Barra multifunzione \(finestra di progettazione visiva\) a un progetto  
 Per utilizzare la finestra di progettazione della barra multifunzione, aggiungere un nuovo elemento **Barra multifunzione \(finestra di progettazione visiva\)** al progetto.  Per ulteriori informazioni, vedere [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Quando si aggiunge un nuovo elemento **Barra multifunzione \(finestra di progettazione visiva\)**, in  Visual Studio vengono aggiunti automaticamente i seguenti file al progetto:  
  
-   Un file di codice della barra multifunzione.  Il nome di questo file corrisponde a quello specificato per l'elemento **Barra multifunzione \(finestra di progettazione visiva\)** nella finestra di dialogo **Aggiungi nuovo elemento**.  Aggiungere codice a questo file per gestire gli eventi della barra multifunzione.  
  
-   File di codice della finestra di progettazione della barra multifunzione.  Questo file contiene codice generato dalla finestra di progettazione della barra multifunzione e non deve essere modificato direttamente.  
  
-   File di risorse.  Questo file contiene i valori di proprietà di ogni controllo sulla barra multifunzione.  
  
 Se si dispone già di un elemento **Barra multifunzione \(finestra di progettazione visiva\)** di un altro progetto, è possibile riutilizzarlo nel progetto corrente mediante la finestra di dialogo **Aggiungi elemento esistente**.  
  
##  <a name="DesigningRibbonLayout"></a> Progettazione di una barra multifunzione  
 La finestra di progettazione della barra multifunzione può essere aperta in tre modi diversi:  
  
-   In **Esplora soluzioni** fare doppio clic sul file di codice della barra multifunzione.  
  
-   In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione, quindi scegliere **Visualizza finestra di progettazione**.  
  
-   In **Esplora soluzioni** selezionare il file di codice della barra multifunzione, quindi scegliere **Finestra di progettazione** dal menu **Visualizza**.  
  
 La finestra di progettazione della barra multifunzione contiene una scheda e un gruppo predefiniti,  che tuttavia possono essere rimossi.  Per rimuovere il gruppo predefinito, fare clic con il pulsante destro del mouse su **Group1**, quindi scegliere **Elimina**.  Per rimuovere la scheda predefinita, fare clic con il pulsante destro del mouse su un'area vuota dell'area di progettazione, quindi scegliere **Rimuovi scheda della barra multifunzione**.  
  
 È anche possibile aggiungere schede, gruppi e controlli personalizzati alla finestra di progettazione della barra multifunzione.  Questi controlli sono disponibili nel gruppo **Controlli barra multifunzione di Office** della **Casella degli strumenti**.  Per aggiungere i controlli del gruppo **Controlli barra multifunzione di Office** alla finestra di progettazione della barra multifunzione, è possibile utilizzare tre modalità:  
  
-   Trascinare un controllo in un'area appropriata della finestra di progettazione della barra multifunzione.  
  
-   Fare clic su un controllo e quindi su un'area appropriata della finestra di progettazione della barra multifunzione.  
  
-   Selezionare un'area appropriata nella finestra di progettazione, quindi fare doppio clic su un controllo nella **Casella degli strumenti**.  
  
### Flusso di lavoro per la progettazione della barra multifunzione  
 Per progettare il layout della barra multifunzione, seguire questi passaggi di base:  
  
1.  [Aggiungere una scheda personalizzata alla barra multifunzione](#AddTabToRibbon).  
  
2.  [Aggiungere gruppi alla scheda](#AddGroupsToTab).  
  
3.  [Aggiungere controlli ai gruppi](#AddControlsToGroups).  
  
 I controlli possono essere rilasciati solo nei gruppi. Non è possibile trascinare un controllo direttamente in una scheda o nella barra multifunzione.  I gruppi possono essere rilasciati solo nelle schede. Non è possibile trascinare un gruppo direttamente in una barra multifunzione.  
  
 Disporre i controlli trascinandoli nelle posizioni corrette.  È possibile impostare le proprietà di un controllo utilizzando la finestra **Proprietà**.  
  
 Non è possibile trascinare i controlli da una scheda all'altra nella barra multifunzione.  Se si desidera spostare un controllo in un'altra scheda, è necessario utilizzare il comando **Taglia** per rimuovere il controllo da una scheda e incollarlo in un'altra.  Quando si taglia e si incolla il controllo, il gestore eventi smette di funzionare.  È possibile riconnettere il gestore eventi nella finestra **Proprietà**.  Per ulteriori informazioni, vedere [finestra Proprietà](../ide/reference/properties-window.md).  
  
###  <a name="AddTabToRibbon"></a> Aggiunta di schede personalizzate alla barra multifunzione.  
 Sono disponibili tre modi per aggiungere una scheda personalizzata alla barra multifunzione:  
  
-   Aggiungere una scheda dalla **Casella degli strumenti**.  
  
-   Fare clic con il pulsante destro del mouse sulla finestra di progettazione della barra multifunzione, quindi scegliere **Aggiungi scheda della barra multifunzione**.  
  
-   Aprire l'**editor della raccolta Tab**, quindi scegliere **Aggiungi**.  
  
     Per aprire l'**editor della raccolta Tab**, nella finestra **Proprietà** selezionare la proprietà **Tabs**, quindi fare clic sul pulsante con i puntini di sospensione ![Ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.png "Ellisse di ASP.NET Mobile Designer").  
  
 Dopo l'aggiunta di una scheda, è possibile aggiungere gruppi che contengano i controlli.  
  
#### Rimozione di schede personalizzate dalla barra multifunzione  
 Sono disponibili tre modi per rimuovere una scheda personalizzata dalla barra multifunzione:  
  
-   Fare clic con il pulsante destro del mouse sulla finestra di progettazione, quindi scegliere **Rimuovi scheda della barra multifunzione**.  
  
-   Nel riquadro **Comandi** della finestra **Proprietà** fare clic su **Rimuovi scheda della barra multifunzione**.  
  
-   Aprire l'**editor della raccolta Tab**, selezionare la scheda, quindi scegliere **Rimuovi**.  
  
#### Modifica della posizione di una scheda nella barra multifunzione  
 È possibile modificare l'ordine delle schede personalizzate in una barra multifunzione.  È anche possibile posizionare le schede personalizzate prima o dopo una scheda incorporata nella barra multifunzione.  Per ulteriori informazioni, vedere [Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### Personalizzazione delle schede incorporate nella barra multifunzione  
 Una scheda incorporata rappresenta una scheda già presente sulla barra multifunzione di un'applicazione Microsoft Office.  Ad esempio, la scheda **Dati** è una scheda incorporata in Excel.  
  
 È possibile aggiungere gruppi e controlli a una scheda incorporata.  Per impostazione predefinita, un gruppo personalizzato viene visualizzato come ultimo gruppo in una scheda incorporata, anche se è possibile spostarlo prima o dopo di un gruppo incorporato nella scheda.  
  
 Non è possibile rimuovere i gruppi incorporati.  
  
 Per informazioni dettagliate su come personalizzare una scheda incorporata, vedere [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Aggiunta di gruppi a una scheda  
 I gruppi organizzano in modo logico i controlli sulla barra multifunzione.  Aggiungere i gruppi alle schede  e tutti gli altri controlli al gruppo.  
  
###  <a name="AddControlsToGroups"></a> Aggiunta di controlli ai gruppi  
 Aggiungere uno o più controlli a un gruppo.  Nella tabella riportata di seguito viene descritto ciascun controllo.  
  
|Controllo|Descrizione|  
|---------------|-----------------|  
|**Box**|Contenitore che organizza i controlli in un gruppo.  È possibile aggiungere qualsiasi controllo a una casella, ad eccezione di un separatore, di un gruppo o di una scheda.  Una casella può essere orizzontale o verticale.|  
|**Button**|Pulsante che avvia un'azione.  È possibile aggiungere un pulsante a un gruppo, a un gruppo di pulsanti, a un elenco a discesa, a una raccolta, a un menu o a un pulsante di menu combinato.|  
|**ButtonGroup**|Gruppo che contiene uno o più pulsanti, interruttori, menu, pulsanti di menu combinato e raccolte.  È possibile aggiungere un gruppo di pulsanti a un gruppo o a un menu.|  
|**CheckBox**|Casella selezionata o deselezionata per attivare o disattivare un'opzione.|  
|**ComboBox**|Casella di modifica a cui è associata una casella di riepilogo.  Gli utenti possono digitare o selezionare le proprie preferenze.  Nella casella viene visualizzata la selezione corrente.  Utilizzare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> per aggiungere e rimuovere elementi in fase di esecuzione prima o dopo il caricamento della barra multifunzione nell'applicazione Office.|  
|**DropDown**|Elenco di elementi selezionabili dall'utente.  L'utente non può digitare un nuovo elemento in un elenco a discesa.<br /><br /> Utilizzare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> per aggiungere elementi all'elenco.  È possibile aggiungere e rimuovere elementi in fase di esecuzione.<br /><br /> Utilizzare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> per aggiungere pulsanti all'elenco.  Non è possibile, tuttavia, aggiungere e rimuovere pulsanti in fase di esecuzione dopo il caricamento della barra multifunzione nell'applicazione Office.|  
|**EditBox**|Casella in cui l'utente può digitare testo.|  
|**Gallery**|Menu che presenta una matrice o una griglia di scelte visive selezionabili dagli utenti.  È possibile controllare il layout delle selezioni nel menu.  Utilizzare le proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> per specificare il numero di righe e di colonne in cui verranno visualizzati gli elementi e i pulsanti della raccolta.|  
|**Etichetta**|Testo che è possibile utilizzare per identificare i controlli sulla barra multifunzione.|  
|**Menu**|Elenco a discesa che può contenere uno dei seguenti controlli:<br /><br /> -   Button<br />-   Casella di controllo<br />-   Gallery<br />-   Menu<br />-   Pulsante di menu combinato<br />-   Toggle button<br />-   Separatore<br /><br /> Per aggiungere un controllo a un menu nella finestra di progettazione della barra multifunzione, fare clic sulla freccia in giù nel menu in modo da esporre l'area di progettazione del menu.  È quindi possibile trascinare i controlli della barra multifunzione dalla **Casella degli strumenti** nel menu.  Per disporre i controlli, trascinarli nelle posizioni desiderate.<br /><br /> Per aggiungere controlli all'oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo il caricamento della barra multifunzione nell'applicazione Office, è necessario impostare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> su **true** prima del caricamento della barra multifunzione.  Per informazioni su come eseguire questa operazione, vedere [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).|  
|**Separatore**|Barra sottile utilizzata per separare gli elementi in un elenco.  Quando aggiunta a un gruppo, la barra è verticale.  Quando aggiunta a un menu, la barra è orizzontale.|  
|**SplitButton**|Pulsante a cui è associato un menu.  Un pulsante di menu combinato può contenere uno dei seguenti controlli:<br /><br /> -   Button<br />-   Casella di controllo<br />-   Gallery<br />-   Menu<br />-   Pulsante di menu combinato<br />-   Toggle button<br />-   Separatore<br /><br /> Analogamente al menu, il pulsante di menu combinato dispone di una propria area di progettazione.  Tuttavia, a differenza di un menu, è possibile solo aggiornare gli elementi in un pulsante di menu combinato prima del caricamento della barra multifunzione nell'applicazione Office.  Per informazioni su come aggiornare gli elementi in un pulsante di menu combinato, vedere [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Pulsante visualizzato come premuto o non premuto.|  
  
##  <a name="HandleEventsSetProperties"></a> Gestione di eventi e impostazione di proprietà  
 La finestra di progettazione della barra multifunzione consente di impostare le proprietà dei controlli in fase di progettazione utilizzando la finestra **Proprietà**.  Inoltre, la barra multifunzione espone un modello a oggetti fortemente tipizzato che è possibile utilizzare per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.  
  
 È possibile fare doppio clic su uno qualsiasi dei controlli contenuti nella finestra di progettazione per aprire un gestore eventi per l'evento predefinito del controllo.  Tramite la finestra **Proprietà** è possibile creare gestori eventi per tutti gli altri eventi di controllo.  
  
 Le proprietà e gli eventi della barra multifunzione si trovano nello spazio dei nomi <xref:Microsoft.Office.Tools.Ribbon>.  L'elemento **Barra multifunzione \(finestra di progettazione visiva\)** aggiunge automaticamente un riferimento a questo assembly nel progetto e inserisce l'istruzione **using** o **Imports** appropriata all'inizio del file di codice della barra multifunzione.  
  
 Per informazioni sulla gestione degli eventi della barra multifunzione e sull'impostazione delle proprietà dei controlli di tale barra in fase di esecuzione, vedere [Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Personalizzazione della visualizzazione Backstage  
 È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere i controlli al menu visualizzato quando si fa clic sulla scheda **File**.  Questo menu viene chiamato la visualizzazione Backstage.  
  
 Non è possibile posizionare controlli prima o dopo i controlli incorporati, utilizzando la finestra di progettazione della barra multifunzione.  Un controllo incorporato è un controllo già disponibile nella visualizzazione Backstage.  Se si desidera posizionare controlli prima o dopo i controlli incorporati, è necessario utilizzare una barra multifunzione XML.  Per ulteriori informazioni sulla **Barra multifunzione \(XML\)**, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere le pagine relative all'[introduzione alla visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e alla [personalizzazione della visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Per informazioni su come aggiungere controlli alla visualizzazione Backstage, vedere [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Accessibilità nella finestra di progettazione della barra multifunzione  
 È possibile utilizzare i tasti di scelta rapida per spostare i controlli nella finestra di progettazione della barra multifunzione.  Alcuni tasti di scelta rapida si applicano a tutti i controlli, mentre altri si applicano solo ai controlli che dispongono di menu.  
  
 Nella tabella riportata di seguito vengono mostrati i tasti di scelta rapida che si applicano a tutti i controlli.  
  
|Azione|Tasto di scelta rapida|  
|------------|----------------------------|  
|Spostamento di un controllo prima del controllo precedente nell'elenco.|CTRL\+freccia SU<br /><br /> CTRL\+freccia SINISTRA|  
|Spostamento di un controllo dopo il controllo successivo nell'elenco.|CTRL\+freccia GIÙ<br /><br /> CTRL\+freccia DESTRA|  
|Spostamento della selezione da un controllo all'altro nello stesso gruppo.  Nel caso di un pannello a discesa, spostamento tra il controllo padre e i controlli in tale pannello.|UP<br /><br /> DOWN|  
|Scorrimento di tutti i controlli in ordine discendente.|TAB|  
|Scorrimento di tutti i controlli in ordine ascendente.|MAIUSC\+TAB|  
|Eliminazione del controllo o dell'insieme di controlli selezionati.|CANC|  
|Copia dei controlli selezionati.|CTRL\+C|  
|Taglio dei controlli selezionati.|CTRL\+X|  
|Operazione di Incolla dei controlli dagli Appunti.|CTRL\+V|  
|Selezione della **Casella degli strumenti**.|CTRL\+ALT\+X|  
|Selezione del componente padre.|ESC|  
  
 Nella tabella riportata di seguito vengono mostrati i tasti di scelta rapida che si applicano solo al menu Microsoft Office, a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> e a <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.  
  
|Azione|Tasto di scelta rapida|  
|------------|----------------------------|  
|Selezione del controllo padre nel caso in cui il pannello a discesa sia aperto e sia selezionato un controllo.|LEFT|  
|Chiusura del pannello a discesa nel caso in cui sia aperto e sia selezionato il controllo padre.|LEFT|  
|Apertura del pannello a discesa.|RIGHT|  
|Selezione del primo controllo nel pannello a discesa nel caso in cui sia aperto.|RIGHT|  
|Chiusura di un pannello a discesa.|ESC|  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  