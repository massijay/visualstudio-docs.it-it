---
title: "Programmazione delle personalizzazioni a livello di documento | Microsoft Docs"
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
  - "Sheet3"
  - "thisWorkbook"
  - "thisDocument"
  - "Sheet1"
  - "Sheet2"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ThisDocument (classe)"
  - "Sheet3 (classe)"
  - "ThisWorkbook (classe)"
  - "scrittura di codice per soluzioni Office"
  - "programmazione [sviluppo per Office in Visual Studio], personalizzazione a livello di documento"
  - "Sheet1 (classe)"
  - "applicazioni di Office [sviluppo per Office in Visual Studio], personalizzazione a livello di documento"
  - "Sheet2 (classe)"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], programmazione"
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], personalizzazione a livello di documento"
ms.assetid: 6c421055-7bea-4db4-a4c9-539b8c78d4ee
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Programmazione delle personalizzazioni a livello di documento
  Quando si estende Microsoft Office Word o Microsoft Office Excel usando una personalizzazione a livello di documento è possibile eseguire le attività seguenti:  
  
-   Automazione dell'applicazione con il relativo modello a oggetti  
  
-   Aggiunta di controlli all'area di un documento  
  
-   Chiamata a codice Visual Basic, Applications Edition \(VBA\) contenuto nel documento dall'assembly di personalizzazione  
  
-   Chiamata a codice contenuto nell'assembly di personalizzazione da VBA  
  
-   Gestione di determinati aspetti di un documento anche se si trova in un server in cui non è stato installato Microsoft Office  
  
-   Personalizzazione dell'interfaccia utente di un'applicazione  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Alcuni aspetti della scrittura del codice nei progetti a livello di documento presentano delle differenze rispetto ad altri tipi di progetti in Visual Studio. Molte di queste differenze sono causate dalla modalità di esposizione dei modelli a oggetti di Office al codice gestito. Per altre informazioni, vedere [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md).  
  
 Per informazioni generali sulle personalizzazioni a livello di documento e su altri tipi di soluzioni che è possibile creare usando gli strumenti di sviluppo di Office in Visual Studio, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
## Uso delle classi generate nei progetti a livello di documento  
 Quando si crea un progetto a livello di documento, in Visual Studio viene generata automaticamente nel progetto una classe utilizzabile come base iniziale di scrittura del codice. Visual Studio genera classi differenti per Word ed Excel:  
  
-   Per impostazione predefinita, nei progetti a livello di documento di Word la classe viene denominata `ThisDocument`.  
  
-   Per i progetti a livello di documento di Excel vengono generate più classi: una per la cartella di lavoro e una per ogni foglio di lavoro. Per impostazione predefinita, queste classi vengono denominate come segue:  
  
    -   `ThisWorkbook`  
  
    -   `Sheet1`  
  
    -   `Sheet2`  
  
    -   `Sheet3`  
  
 La classe generata contiene gestori eventi che vengono chiamati quando il documento viene aperto o chiuso. Per eseguire il codice all'apertura del documento, aggiungerlo nel gestore dell'evento `Startup`. Per eseguire il codice subito prima della chiusura del documento, aggiungerlo al gestore dell'evento `Shutdown`. Per altre informazioni, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
### Informazioni sulla progettazione delle classi generate  
 Nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], i tipi di elemento host in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sono le interfacce, quindi le classi generate non possono derivare da esse la loro implementazione. Al contrario, le classi generate derivano la maggior parte dei loro membri dalle classi base seguenti:  
  
-   `ThisDocument`: deriva da <xref:Microsoft.Office.Tools.Word.DocumentBase>.  
  
-   `ThisWorkbook`: deriva da <xref:Microsoft.Office.Tools.Excel.WorkbookBase>.  
  
-   `Sheet` *n*: deriva da <xref:Microsoft.Office.Tools.Excel.WorksheetBase>.  
  
 Queste classi base reindirizzano tutte le chiamate ai loro membri a implementazioni interne delle interfacce di elementi host corrispondenti in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Ad esempio, se si chiama il metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.Protect%2A> della classe `ThisDocument`, la classe <xref:Microsoft.Office.Tools.Word.DocumentBase> reindirizzerà questa chiamata all'implementazione interna dell'interfaccia di <xref:Microsoft.Office.Tools.Word.Document> in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## Accesso al modello a oggetti dell'applicazione host  
 Per accedere al modello a oggetti dell'applicazione host occorre usare i membri della classe generata nel progetto. Ognuna di queste classi corrisponde a un oggetto nel modello a oggetti di Excel o Word. In particolare, le classi sono quasi identiche in termini di proprietà, metodi ed eventi. Ad esempio, la classe `ThisDocument` di un progetto a livello di documento di Word fornisce la maggior parte dei membri disponibili nell'oggetto <xref:Microsoft.Office.Interop.Word.Document> del modello a oggetti di Word.  
  
 L'esempio di codice seguente illustra come usare il modello a oggetti di Word per salvare il documento appartenente a una personalizzazione a livello di documento di Word. Questo esempio è destinato a essere eseguito dalla classe `ThisDocument`.  
  
```vb  
Me.Save()  
```  
  
```csharp  
this.Save();  
```  
  
 Per eseguire la stessa operazione dall'esterno della classe `ThisDocument`, usare l'oggetto `Globals` per accedere alla classe `ThisDocument`. Ad esempio, per includere un pulsante **Salva** nell'interfaccia utente del riquadro delle azioni è possibile aggiungere questo codice a un file di codice del riquadro delle azioni.  
  
```vb  
Globals.ThisDocument.Save()  
```  
  
```csharp  
Globals.ThisDocument.Save();  
```  
  
 Dal momento che la classe `ThisDocument` ottiene la maggior parte dei suoi membri dall'elemento host <xref:Microsoft.Office.Tools.Word.Document>, il metodo `Save` chiamato in questo codice è di fatto il metodo <xref:Microsoft.Office.Tools.Word.Document.Save%2A> dell'elemento host <xref:Microsoft.Office.Tools.Word.Document>. Questo metodo corrisponde al metodo <xref:Microsoft.Office.Interop.Word._Document.Save%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> del modello a oggetti di Word.  
  
 Per altre informazioni sull'uso dei modelli a oggetti di Word ed Excel, vedere [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md) e [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
 Per altre informazioni sull'oggetto `Globals`, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
## Aggiunta di controlli ai documenti  
 Per personalizzare l'interfaccia utente di un documento è possibile aggiungere controlli Windows Form o *controlli host* all'area del documento. Con la combinazione di set di controlli diversi e con la scrittura di codice, è possibile associare i controlli ai dati, raccogliere le informazioni relative all'utente e rispondere alle azioni utente.  
  
 I controlli host sono classi che estendono alcuni degli oggetti del modello a oggetti di Word ed Excel. Ad esempio, il controllo host <xref:Microsoft.Office.Tools.Excel.ListObject> fornisce tutte le funzionalità dell'oggetto <xref:Microsoft.Office.Interop.Excel.ListObject> di Excel. Tuttavia, il controllo host <xref:Microsoft.Office.Tools.Excel.ListObject> presenta anche eventi e funzionalità di data binding aggiuntivi.  
  
 Per altre informazioni, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md) e [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## Combinazione di VBA con le personalizzazioni a livello di documento  
 È possibile usare codice VBA in un documento appartenente a una personalizzazione a livello di documento. È possibile chiamare codice VBA nel documento dall'assembly di personalizzazione e anche configurare il progetto in modo da consentire al codice VBA nel documento di chiamare il codice nell'assembly di personalizzazione.  
  
 Per altre informazioni, vedere [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md).  
  
## Gestione di documenti in un server  
 Diversi aspetti della personalizzazione a livello di documento possono essere gestiti anche nei server in cui non è stato installato Microsoft Office Word oppure Microsoft Office Excel. È ad esempio possibile accedere e apportare modifiche ai dati memorizzati nella cache dei dati di un documento. È anche possibile gestire l'assembly di personalizzazione associato al documento. Ad esempio, è possibile rimuovere a livello di codice l'assembly da un documento in modo che quest'ultimo non esegua più il codice.  
  
 Per altre informazioni, vedere [Gestione dei documenti di un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md).  
  
## Personalizzazione dell'interfaccia utente delle applicazioni di Microsoft Office  
 È possibile personalizzare l'interfaccia utente di Word ed Excel nei modi seguenti usando una personalizzazione a livello di documento:  
  
-   Aggiungere controlli host o controlli Windows Form alla superficie del documento.  
  
     Per altre informazioni, vedere [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md), [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md) e [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Aggiungere un riquadro Azioni al documento.  
  
     Per altre informazioni, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md).  
  
-   Aggiungere schede personalizzate alla barra multifunzione.  
  
     Per altre informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
-   Aggiungere gruppi personalizzati a una scheda incorporata nella barra multifunzione.  
  
     Per altre informazioni, vedere [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md).  
  
 Per altre informazioni sulla personalizzazione dell'interfaccia utente delle applicazioni di Microsoft Office, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Recupero degli oggetti estesi dagli oggetti nativi di Office nelle personalizzazioni a livello di documento  
 Molti gestori degli eventi di Office ricevono un oggetto nativo di Office che rappresenta la cartella di lavoro, il foglio di lavoro o il documento che ha generato l'evento. In alcuni casi, è necessario eseguire il codice solo se l'evento è stato generato dalla cartella di lavoro o dal documento della personalizzazione a livello di documento. Ad esempio, in una personalizzazione a livello di documento per Excel, è necessario eseguire il codice quando l'utente attiva uno dei fogli di lavoro nella cartella di lavoro personalizzata, ma non quando l'utente attiva un foglio di lavoro in altre cartelle di lavoro che possono essere aperte contemporaneamente.  
  
 Quando è presente un oggetto nativo di Office, è possibile verificare se tale oggetto è stato esteso in un *elemento host* o in un *controllo host* di una personalizzazione a livello di documento. Gli elementi e i controlli host sono tipi forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che consentono di aggiungere funzionalità a oggetti che esistono a livello nativo nei modelli a oggetti di Word o di Excel \(chiamati *oggetti nativi di Office*\). Collettivamente, gli elementi host e controlli host vengono definiti *oggetti estesi*. Per altre informazioni sugli elementi host e i controlli host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
## Informazioni sui metodi GetVstoObject e HasVstoObject  
 Per eseguire il test di un oggetto nativo di Office, usare i metodi HasVstoObject e GetVstoObjectnel progetto:  
  
-   Se si vuole determinare se l'oggetto nativo di Office ha un oggetto esteso nella personalizzazione, usare il metodo HasVstoObject. Questo metodo restituisce **true** se l'oggetto nativo di Office ha un oggetto esteso, altrimenti **false**.  
  
-   Se si vuole ottenere l'oggetto esteso per un oggetto nativo di Office, usare il metodo GetVstoObject. Questo metodo restituisce un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject>, <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> se l'oggetto nativo di Office specificato ne ha uno. In caso contrario, GetVstoObject restituisce **null**. Ad esempio, il metodo GetVstoObject restituisce un oggetto <xref:Microsoft.Office.Tools.Word.Document> se l'oggetto <xref:Microsoft.Office.Interop.Word.Document> specificato è l'oggetto sottostante del documento nel progetto documento di Word.  
  
 Nei progetti a livello di documento non è possibile usare il metodo GetVstoObject per creare un nuovo elemento host <xref:Microsoft.Office.Tools.Excel.Workbook>, <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> in fase di esecuzione. Tale metodo può essere usato solo per accedere agli elementi host esistenti generati nel progetto in fase di progettazione. Se si vogliono creare nuovi elementi host in fase di esecuzione, è necessario sviluppare un progetto a livello di applicazione. Per altre informazioni, vedere [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md) e [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Uso dei metodi GetVstoObject e HasVstoObject  
 Per chiamare il metodo HasVstoObject e GetVstoObject, usare il metodo Globals.Factory.GetVstoObject o Globals.Factory.HasVstoObject e passare l'oggetto nativo di Word o di Excel \(ad esempio <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet>\) che si vuole testare.  
  
## Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Combinazione di VBA con le personalizzazioni a livello di documento](../vsto/combining-vba-and-document-level-customizations.md)   
 [Gestione dei documenti di un server utilizzando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  