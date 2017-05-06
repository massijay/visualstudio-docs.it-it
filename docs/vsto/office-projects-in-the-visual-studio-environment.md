---
title: "Progetti di Office in ambiente Visual Studio"
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
  - "VST.ProjectItem.WordDocument"
  - "VST.ProjectItem.ExcelWorkbook"
  - "VST.ProjectItem.ExcelTemplate"
  - "VST.ProjectItem.ExcelSheet"
  - "VST.ProjectItem.BlueprintCode"
  - "VST.ProjectItem.Word"
  - "VST.ProjectItem.Excel"
  - "VST.ProjectItem.AddinProject"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Excel.Design.WorksheetDesigner"
  - "VST.ProjectItem.ExtendedBluePrint"
  - "VST.ProjectItem.WordTemplate"
  - "Designer_Microsoft.VisualStudio.OfficeTools.Word.Design.DocumentDesigner"
  - "VST.Designer.ExcelVST.Designer.Word"
  - "VST.ProjectItem.ExtendedBlueprintCode"
  - "VST.ProjectItem.BluePrint"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "documenti [sviluppo per Office in Visual Studio]"
  - "file nascosti [sviluppo per Office in Visual Studio]"
  - "file di progetto [sviluppo per Office in Visual Studio], nascosto"
  - "sviluppo per Office in Visual Studio, documenti in Visual Studio"
  - "visualizzazione Progettazione, Excel"
  - "finestre di progettazione sviluppo per Office in Visual Studio"
  - "documenti di Office [sviluppo per Office in Visual Studio]"
  - "documenti di Office [sviluppo per Office in Visual Studio], informazioni sui documenti in Visual Studio"
  - "finestre di progettazione [sviluppo per Office in Visual Studio]"
  - "finestra di progettazione di Word"
  - "Word [sviluppo per Office in Visual Studio], finestra di progettazione di Word"
  - "Visual Studio, documenti di Office"
  - "fogli di lavoro [sviluppo per Office in Visual Studio]"
  - "VST.Designer.ExcelVST.Designer.Word"
ms.assetid: 4bff36c9-4edd-4b28-89e6-0ea9f6caca02
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Progetti di Office in ambiente Visual Studio
  L'esperienza di sviluppo relativa ai progetti di Microsoft Office è simile a quella per altri tipi di progetti in Visual Studio, ad esempio progetti Windows Form. Quando si crea o si apre un progetto di Office, gli elementi del progetto vengono visualizzati in **Esplora soluzioni**. Per i progetti a livello di documento, il documento \(ossia il documento di Word o la cartella di lavoro di Excel\) viene aperto in Visual Studio e funziona come una finestra di progettazione visiva.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Elementi di progetto in Esplora soluzioni  
 In un progetto a livello di documento, in **Esplora soluzioni** sono illustrati gli elementi predefiniti seguenti:  
  
-   I nodi per il documento, la cartella di lavoro e i fogli personalizzati per il progetto. Questi nodi fungono da contenitori per i file di codice associati al documento, alla cartella di lavoro e ai fogli.  
  
-   I file di codice associati al documento, alla cartella di lavoro e ai fogli personalizzato dal progetto. Nei progetti di Word i file di codice vengono associati al documento o al modello di Word. Nei progetti di Excel i file di codice vengono associati alla cartella di lavoro o al modello di Excel e a ogni foglio di lavoro e foglio grafico nella cartella di lavoro o nel modello.  
  
-   I file di progetto nascosti per i quali non è prevista la modifica diretta. Per altre informazioni, vedere [File di progetto nascosti](#hiddenfiles).  
  
 In un progetto di componente aggiuntivo VSTO, in **Esplora soluzioni** sono illustrati gli elementi predefiniti seguenti:  
  
-   Il nodo dell'applicazione. Questo nodo ha lo stesso nome dell'applicazione host, ad esempio **Word**, **Excel** oppure **Outlook**. Il nodo dell'applicazione contiene il file di codice ThisAddIn. Fornisce anche la proprietà **Spazio dei nomi per elemento host**. Per altre informazioni su questa proprietà, vedere [Proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).  
  
-   Il file di codice ThisAddIn. Questo file contiene la classe `ThisAddIn` generata per il componente aggiuntivo VSTO. Per altre informazioni su questa classe, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   I file di progetto nascosti per i quali non è prevista la modifica diretta. Per altre informazioni, vedere [File di progetto nascosti](#hiddenfiles).  
  
### Certificati temporanei  
 I progetti di Office includono anche un certificato temporaneo denominato *Nome progetto\_TemporaryKey.pfx*. Questo certificato viene usato per firmare i manifesti dell'applicazione e della distribuzione per il progetto durante lo sviluppo. Per altre informazioni, vedere [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md) e [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md).  
  
###  <a name="hiddenfiles"></a> File di progetto nascosti  
 Alcuni file di progetto sono nascosti per impostazione predefinita. Questi file vengono generati da Visual Studio e si differenziano in base al tipo di progetto. Per visualizzare i file nascosti, fare clic su **Mostra tutti i file** in **Esplora soluzioni**.  
  
 Non modificare i file di progetto nascosti. La modifica diretta di questi file non è supportata e potrebbe danneggiare il progetto. I file di progetto nascosti vengono rigenerati ogni volta che vengono apportate determinate modifiche al documento. Se si apportano modifiche manuali a un file di progetto nascosto, tali modifiche vengono perse quando il file viene rigenerato.  
  
## Finestra di progettazione del documento in progetti a livello di documento  
 I progetti a livello di documento per Excel e Word forniscono una finestra di progettazione che ospita il documento associato al progetto in Visual Studio. La finestra di progettazione consente di modificare il documento senza uscire dall'ambiente di Visual Studio.  
  
 Per aprire un documento nella finestra di progettazione, fare doppio clic sul file di codice associato al documento in **Esplora soluzioni**. Ad esempio, per aprire il foglio di lavoro **Foglio1** nella finestra di progettazione in un progetto di Excel, fare doppio clic sul file di codice **Foglio1**.  
  
 Quando si modifica il documento nella finestra di progettazione, è possibile usare la funzionalità nativa dell'applicazione di Office. Ad esempio, è possibile digitare il testo nel documento o in un foglio di lavoro oppure usare la barra multifunzione per eseguire attività quali l'aggiunta di una tabella o di un grafico. Per impostazione predefinita, per i tasti di scelta rapida viene usato automaticamente il mapping di Visual Studio. Per usare invece i mapping dei tasti di scelta rapida di Office, modificare le impostazioni in corrispondenza del nodo **Impostazioni tastiera Microsoft Office** nella finestra di dialogo **Opzioni** del menu **Strumenti**.  
  
### Controlli nei documenti  
 È possibile trascinare i *controlli host* e i controlli Windows Form dalla **Casella degli strumenti** di Visual Studio all'area di progettazione del documento. I controlli host sono versioni specifiche di oggetti di Office, quali controlli del contenuto di Word e intervalli di Excel, che possono essere usati in progetti di Office creati tramite Visual Studio. I controlli host dispongono di funzionalità aggiuntive che non sono disponibili negli oggetti di Office corrispondenti, ad esempio associazione dati e ulteriori eventi.  
  
 Per altre informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md) e [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
### Fogli e cartelle di lavoro di Excel nella finestra di progettazione  
 Quando si apre un foglio di lavoro nella finestra di progettazione, è possibile modificarlo come se fosse aperto direttamente in Excel. Se si fa doppio clic su una cella del foglio di lavoro, la cella passa alla modalità di modifica. Se si fa doppio clic su una cella contenente un controllo host, viene aperto l'editor di codice e in Visual Studio viene generato il gestore eventi predefinito per il controllo. Per passare agli altri fogli di lavoro, è possibile fare clic sulle schede dei fogli di lavoro nella parte inferiore della finestra di progettazione.  
  
 Quando si apre la cartella di lavoro nella finestra di progettazione, non è visualizzata alcuna area di progettazione. La visualizzazione Progettazione per la cartella di lavoro è una barra dei componenti di grandi dimensioni che occupa la finestra di progettazione.  
  
 Alla cartella di lavoro e a ciascun foglio di lavoro è associato un file di codice. Ogni file di codice contiene una classe *elemento host* generata che rappresenta la cartella di lavoro o il foglio. Per altre informazioni, vedere [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md).  
  
### Documenti di Word nella finestra di progettazione  
 Quando si apre il documento nella finestra di progettazione, è possibile modificarlo come se fosse aperto direttamente in Word. Se si fa doppio clic su una parola nel documento, tale parola viene selezionata. Se tuttavia la parola è all'interno di un controllo host, viene aperto l'editor di codice e in Visual Studio viene generato il gestore eventi predefinito per il controllo.  
  
 Al documento è associato un file di codice. Il file di codice contiene una classe *elemento host* generata che rappresenta il documento. Per altre informazioni, vedere [Elemento host Document](../vsto/document-host-item.md).  
  
### Modalità progettazione rispetto a modalità runtime  
 Se aperto nell'ambiente Visual Studio, il documento è sempre in *modalità di progettazione*. È possibile eseguire alcune attività, ad esempio il trascinamento di un controllo host nell'area del documento, solo in modalità di progettazione.  
  
 Per visualizzare il documento in *modalità di esecuzione*, è necessario aprire l'applicazione e il documento all'esterno di Visual Studio. È anche possibile compilare ed eseguire il progetto, che aprirà automaticamente il documento e l'applicazione all'esterno di Visual Studio.  
  
## Editor di codice  
 L'editor di codice consente di visualizzare e modificare i file di codice visibili nella soluzione. Questi file contengono il codice che definisce il comportamento della soluzione.  
  
 Per altre informazioni sull'editor di codice, vedere [Scrittura di codice nell'Editor di testo e del codice](../ide/writing-code-in-the-code-and-text-editor.md). Per altre informazioni su come scrivere codice nei progetti di Office, vedere [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md).  
  
## Finestra Proprietà  
 La finestra **Proprietà** mostra le proprietà per gli elementi del progetto selezionati in **Esplora soluzioni** e per gli elementi dell'interfaccia utente selezionati nella finestra di progettazione, ad esempio i controlli o il documento in un progetto a livello di documento. Alcune proprietà sono specifiche dell'applicazione e del documento, mentre altre sono identiche per tutti i progetti.  
  
## Finestra Origini dati  
 È possibile usare la finestra **Origini dati** all'interno dei progetti di Office a livello di documento per trascinare un'origine dati nel documento e creare un controllo associato all'origine dati. Per altre informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../Topic/Binding%20controls%20to%20data%20in%20Visual%20Studio.md).  
  
## Vedere anche  
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)   
 [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Proprietà nei progetti di Office](../vsto/properties-in-office-projects.md)  
  
  