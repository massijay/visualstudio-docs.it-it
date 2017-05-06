---
title: "Cenni preliminari sulla barra multifunzione"
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
  - "barra multifunzione personalizzata, più barre multifunzione"
  - "personalizzazione della barra multifunzione, più barre multifunzione"
  - "barra multifunzione [sviluppo per Office in Visual Studio]"
  - "barra multifunzione [sviluppo per Office in Visual Studio], informazioni sulla barra multifunzione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], più barre multifunzione"
  - "barre degli strumenti [sviluppo per Office in Visual Studio]"
  - "barre degli strumenti [sviluppo per Office in Visual Studio], barra multifunzione"
ms.assetid: 2bdef092-190d-47e3-9440-e862b95dacaa
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Cenni preliminari sulla barra multifunzione
  La barra multifunzione rappresenta uno strumento per organizzare i comandi correlati in modo da semplificarne la ricerca.  Sulla barra i comandi vengono visualizzati come controlli,  organizzati in *gruppi* disposti lungo una striscia orizzontale all'estremità superiore della finestra di un'applicazione.  I gruppi correlati sono organizzati in schede.  
  
 La maggior parte delle funzionalità che erano accessibili con i menu e le barre degli strumenti nelle versioni precedenti di Microsoft Office ora è accessibile con la barra multifunzione.  Per altre informazioni, vedere l'articolo tecnico [Panoramica per lo sviluppatore dell'interfaccia utente di Microsoft Office System 2007](http://go.microsoft.com/fwlink/?LinkID=70860).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Personalizzazione della barra multifunzione di Microsoft Office  
 Per personalizzare la barra multifunzione, aggiungere uno dei seguenti elementi della barra al progetto di Office:  
  
-   **Barra multifunzione \(finestra di progettazione visiva\)**  
  
-   **Barra multifunzione \(XML\)**  
  
 Ad esempio, per personalizzare la barra multifunzione di Excel, aggiungere un elemento di tale barra a un progetto di componente aggiuntivo VSTO per Excel.  
  
### Elemento Barra multifunzione \(finestra di progettazione visiva\)  
 L'elemento **Barra multifunzione \(finestra di progettazione visiva\)** fornisce strumenti avanzati che semplificano la progettazione e lo sviluppo di una barra multifunzione personalizzata.  Usare l'elemento **Barra multifunzione \(finestra di progettazione visiva\)** per personalizzare la barra multifunzione nei modi seguenti:  
  
-   Aggiunta di schede personalizzate o incorporate a una barra multifunzione  
  
-   Aggiunta di gruppi personalizzati a una scheda personalizzata o incorporata  
  
    > [!NOTE]  
    >  Una scheda o un gruppo incorporato rappresentano una scheda o un gruppo già presenti sulla barra multifunzione di un'applicazione Microsoft Office.  Ad esempio, la scheda **Dati** è una scheda incorporata in Excel.  Il gruppo **Connessioni** è un gruppo incorporato nella scheda **Dati**.  
  
-   Aggiunta di controlli personalizzati a un gruppo personalizzato.  
  
-   Aggiunta di controlli personalizzati alla visualizzazione backstage.  
  
 Per altre informazioni su come personalizzare una barra multifunzione usando l'elemento **Barra multifunzione \(finestra di progettazione visiva\)**, vedere [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md).  
  
### Elemento Barra multifunzione \(XML\)  
 Usare l'elemento **Barra multifunzione \(XML\)** per personalizzare la barra multifunzione in un modo non supportato dall'elemento **Barra multifunzione \(finestra di progettazione visiva\)**.  Usare l'elemento **Barra multifunzione \(XML\)** per personalizzare la barra multifunzione nei modi seguenti:  
  
-   Aggiunta di gruppi *incorporati* a una scheda personalizzata o incorporata.  
  
-   Aggiunta di controlli incorporati a un gruppo personalizzato.  
  
-   Aggiunta di codice personalizzato per eseguire l'override dei gestori eventi dei controlli incorporati.  
  
-   Personalizzazione della barra di accesso rapido.  
  
-   Condivisione di una personalizzazione della barra multifunzione tra diversi componenti aggiuntivi VSTO usando un ID completo.  
  
 Per altre informazioni su come personalizzare la barra multifunzione usando l'elemento **Barra multifunzione \(XML\)**, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
## Esportazione di una barra multifunzione dalla finestra di progettazione in un elemento XML della barra  
 Se si crea una barra multifunzione usando la relativa finestra di progettazione e si decide quindi di personalizzare la barra in modi non supportati dall'elemento **Barra multifunzione \(finestra di progettazione visiva\)**, è possibile esportare la barra multifunzione in XML.  
  
 In Visual Studio viene automaticamente creato un elemento **Barra multifunzione \(XML\)** e il file XML della barra multifunzione viene popolato con elementi e attributi per ogni controllo della barra.  
  
 Non tutte le proprietà contenute nella finestra **Proprietà** della finestra di progettazione della barra multifunzione vengono trasferite nel file XML della barra.  Ad esempio, in Visual Studio non viene esportato il valore della proprietà **Image** o **Text**.  Questa situazione si verifica perché è necessario creare un metodo di callback nel file di codice della barra multifunzione del progetto esportato per assegnare un'immagine o impostare il testo di un controllo.  In Visual Studio non vengono generati automaticamente metodi di callback come parte del processo di esportazione.  
  
 In più, i valori di proprietà predefiniti rimasti invariati non vengono visualizzati nel file XML risultante della barra multifunzione.  
  
 Per altre informazioni su come esportare la barra multifunzione in XML, vedere [Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### Aggiornamento del codice  
 Viene aggiunto un nuovo file di codice della barra multifunzione a **Esplora soluzioni**.  Questo file contiene la classe XML della barra multifunzione.  È necessario creare metodi di callback nell'area `Ribbon Callbacks` di questa classe per gestire le azioni dell'utente, ad esempio la selezione di un pulsante.  Spostare il codice dai gestori eventi in questi metodi di callback e modificarlo in modo che usi il modello di programmazione di estendibilità della barra multifunzione \(RibbonX\).  Per altre informazioni, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
 È anche necessario aggiungere codice alla classe `ThisAddIn`, `ThisWorkbook` o `ThisDocument` che esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe XML della barra multifunzione all'applicazione Office.  
  
 Per altre informazioni, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
## Aggiunta di più elementi della barra multifunzione a un progetto  
 È possibile aggiungere più elementi della barra multifunzione a un singolo progetto.  Questa operazione è utile per eseguire una delle due attività seguenti:  
  
-   Creazione di barre multifunzione per i *controlli* Outlook.  Per altre informazioni, vedere [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
    > [!NOTE]  
    >  Un controllo rappresenta una finestra che viene aperta quando gli utenti eseguono determinate attività, ad esempio la creazione di un messaggio di posta elettronica.  
  
-   Selezione della barra multifunzione da visualizzare in fase di esecuzione.  
  
### Selezione delle barre multifunzione da visualizzare in fase di esecuzione.  
 Dal momento che un progetto può contenere più barre multifunzione, è possibile selezionare quella da visualizzare in fase di esecuzione.  
  
 Per selezionare una barra multifunzione da visualizzare in fase di esecuzione, eseguire l'override del metodo CreateRibbonExtensibilityObject nella classe `ThisAddin`, `ThisWorkbook` o `ThisDocument` del progetto e restituire la barra multifunzione che si vuole visualizzare.  L'esempio seguente controlla il valore di un campo denominato `myCondition` e viene restituita la barra multifunzione appropriata.  
  
> [!NOTE]  
>  La sintassi usata in questo esempio restituisce una barra multifunzione creata con l'elemento **Barra multifunzione \(finestra di progettazione visiva\)**.  La sintassi per la restituzione di una barra multifunzione creata con un elemento **Barra multifunzione \(XML\)** è leggermente diversa.  Per altre informazioni sulla restituzione di un elemento **Barra multifunzione \(XML\)**, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
 Aggiungere il codice seguente:  
  
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Choose_Ribbon/VB/ThisWorkbook.vb#1)]  
  
### Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)|Illustra come personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento **Barra multifunzione \(finestra di progettazione visiva\)** o **Barra multifunzione \(XML\)** a un progetto di Office.|  
|[Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)|Descrive come usare la finestra di progettazione della barra multifunzione per aggiungere schede, gruppi e controlli personalizzati alla barra multifunzione di un'applicazione di Microsoft Office.|  
|[Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando la finestra di progettazione della barra multifunzione.  Questa finestra di progettazione può essere usata per aggiungere e posizionare controlli sulla scheda personalizzata.|  
|[Cenni preliminari sul modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)|Fornisce una panoramica di un modello a oggetti fortemente tipizzato per ottenere e impostare le proprietà dei controlli della barra multifunzione in fase di esecuzione.|  
|[Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)|Illustra come usare il modello a oggetti della barra multifunzione per aggiornare i controlli di una barra multifunzione dopo che la barra multifunzione è stata caricata nell'applicazione Office.|  
|[Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)|Fornisce materiale sussidiario per personalizzare la barra multifunzione in Microsoft Office Outlook.|  
|[Personalizzazione di una barra multifunzione per InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|Fornisce materiale sussidiario per personalizzare la barra multifunzione in Microsoft Office InfoPath.|  
|[Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)|Illustra come mostrare, nascondere o modificare la barra multifunzione e consentire agli utenti di eseguire il codice dai controlli in un riquadro attività personalizzato, un riquadro azioni o un'area del modulo di Outlook.|  
|[Procedura: modificare la posizione di una scheda nella barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)|Illustra come modificare l'ordine delle schede nella barra multifunzione.|  
|[Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)|Illustra come aggiungere gruppi e controlli a una scheda incorporata.|  
|[Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)|Illustra come aggiungere controlli al menu visualizzato quando si sceglie **File**.|  
|[Procedura: aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione](../vsto/how-to-add-a-dialog-box-launcher-to-a-ribbon-group.md)|Illustra come aggiungere un pulsante di visualizzazione della finestra di dialogo a qualsiasi gruppo della barra multifunzione.|  
|[Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)|Illustra come personalizzare la barra multifunzione in modalità avanzate esportandola dalla finestra di progettazione nell'elemento XML della barra multifunzione.|  
|[Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)|Descrive come è possibile personalizzare una barra multifunzione usando l'elemento XML della barra multifunzione.|  
|[Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)|Illustra come creare una scheda personalizzata della barra multifunzione usando l'elemento **Barra multifunzione \(XML\)**.|  
  
  