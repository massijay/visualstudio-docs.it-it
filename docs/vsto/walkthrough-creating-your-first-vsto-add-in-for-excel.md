---
title: "Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel | Microsoft Docs"
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
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], creazione del primo progetto"
  - "sviluppo per Office in Visual Studio, creazione del primo progetto"
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], creazione del primo progetto"
  - "Excel [sviluppo per Office in Visual Studio], creazione del primo progetto"
ms.assetid: a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel
  Questa procedura dettagliata introduttiva descrive come creare un componente aggiuntivo a livello di applicazione per Microsoft Office Excel. Le funzionalità create dall'utente in questo tipo di soluzione sono disponibili per l'applicazione stessa, indipendentemente da quali cartelle di lavoro siano aperte.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto di componente aggiuntivo VSTO per Excel.  
  
-   Scrittura di codice che usa il modello a oggetti di Excel per aggiungere testo a una cartella di lavoro, quando viene salvata.  
  
-   Creazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto completato, per fare in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Creazione del progetto  
  
#### Per creare un nuovo progetto di componente aggiuntivo VSTO per Excel in Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C\#** o **Visual Basic**, quindi espandere **Office\/SharePoint**.  
  
4.  Nel nodo **Office\/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office**.  
  
5.  Nell'elenco relativo ai modelli di progetto, selezionare **Componente aggiuntivo per Excel 2010** o **Componente aggiuntivo per Excel 2013**.  
  
6.  Nella casella **Nome**, digitare **FirstExcelAddIn**.  
  
7.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di creare il progetto **FirstExcelAddIn** e di aprire il file di codice ThisAddIn nell'editor.  
  
## Scrittura di codice per aggiungere testo alla cartella di lavoro salvata  
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di Excel al fine di inserire testo boilerplate nella prima riga del foglio di lavoro attivo. Il foglio di lavoro attivo è quello aperto quando l'utente salva la cartella di lavoro. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisAddIn`. Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di Excel. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md). Il resto della classe `ThisAddIn` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown`. Questi gestori eventi vengono chiamati quando Excel carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO quando viene caricato e per eseguire la pulizia delle risorse usate dal componente aggiuntivo quando viene scaricato. Per altre informazioni, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
#### Aggiungere una riga di testo alla cartella di lavoro salvata  
  
1.  Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn`. Il nuovo codice definisce un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>, che viene generato quando si salva una cartella di lavoro.  
  
     Quando l'utente salva una cartella di lavoro, il gestore eventi aggiunge il nuovo testo all'inizio del foglio di lavoro attivo.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Se si usa C\#, aggiungere il seguente codice obbligatorio al gestore eventi `ThisAddIn_Startup`. Tale codice viene usato per connettere il gestore eventi `Application_WorkbookBeforeSave` all'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Per modificare la cartella di lavoro salvata, gli esempi di codice precedenti usano i seguenti oggetti:  
  
-   Il campo `Application` della classe `ThisAddIn`. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Application> che rappresenta l'istanza corrente di Excel.  
  
-   Il parametro `Wb` del gestore eventi dell'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Il `Wb` parametro consiste in un oggetto <xref:Microsoft.Office.Interop.Excel.Workbook> che rappresenta la cartella di lavoro. Per altre informazioni, vedere [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
## Test del progetto  
  
#### Per testare il progetto  
  
1.  Premere **F5** per compilare ed eseguire il progetto.  
  
     Quando si crea il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Visual Studio crea anche un set di voci del Registro di sistema che permettono a Excel di individuare e caricare il componente aggiuntivo VSTO e configura le impostazioni di sicurezza nel computer di sviluppo per permettere l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
2.  In Excel, salvare la cartella di lavoro.  
  
3.  Verificare che il seguente testo venga aggiunto alla cartella di lavoro.  
  
     **This text was added by using code.**  
  
4.  Chiudere Excel.  
  
## Pulizia del progetto  
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO continuerà a essere eseguito ogni volta che si apre Excel nel computer di sviluppo.  
  
#### Per pulire il progetto completato nel computer di sviluppo  
  
1.  In Visual Studio, nel menu **Compila**, fare clic su **Pulisci soluzione**.  
  
## Passaggi successivi  
 Dopo aver creato un componente aggiuntivo VSTO di base per Excel, è possibile visualizzare altre informazioni su come sviluppare componenti aggiuntivi VSTO in questi argomenti:  
  
-   Attività di programmazione generali che è possibile eseguire in componenti aggiuntivi VSTO: [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Attività di programmazione specifiche per i componenti aggiuntivi VSTO: [Soluzioni Excel](../vsto/excel-solutions.md).  
  
-   Uso del modello a oggetti di Excel: [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md).  
  
-   Personalizzazione dell'interfaccia utente \(UI\) di Excel, ad esempio, aggiungendo una scheda personalizzata alla barra multifunzione oppure creando un riquadro attività personalizzato: [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
-   Compilazione e debug di componenti aggiuntivi VSTO per Excel: [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione di componenti aggiuntivi VSTO per Excel: [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Vedere anche  
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluzioni Excel](../vsto/excel-solutions.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Cenni preliminari sul modello a oggetti di Excel](../vsto/excel-object-model-overview.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  