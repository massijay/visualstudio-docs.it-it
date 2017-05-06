---
title: "Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Word"
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
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], creazione del primo progetto"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], creazione del primo progetto"
  - "sviluppo per Office in Visual Studio, creazione del primo progetto"
  - "Word [sviluppo per Office in Visual Studio], creazione del primo progetto"
ms.assetid: 9d857be7-5c74-4303-baf4-672afc1ea397
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Word
  Questa procedura dettagliata introduttiva illustra come creare un componente aggiuntivo VSTO per Microsoft Office Word.   Le funzionalità create in questo tipo di soluzione sono disponibili per l'applicazione, indipendentemente da quali documenti vengano aperti.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto di componente aggiuntivo VSTO di Word.  
  
-   Scrittura di codice che usa il modello a oggetti di Word per aggiungere testo a un documento quando quest'ultimo viene salvato.  
  
-   Compilazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto completato, in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Creazione del progetto  
  
#### Per creare un nuovo progetto per un componente aggiuntivo VSTO di Word in Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C\#** o **Visual Basic**, quindi espandere **Office\/SharePoint**.  
  
4.  Nel nodo **Office\/SharePoint** espanso selezionare il nodo **Componenti aggiuntivi di Office**.  
  
5.  Nell'elenco dei modelli di progetto scegliere un progetto del componente aggiuntivo VSTO di Word.  
  
6.  Nella casella **Nome** digitare **FirstWordAddIn**.  
  
7.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto **FirstWordAddIn** e apre il file di codice ThisAddIn nell'editor.  
  
## Scrittura di codice per aggiungere testo nel documento salvato  
 Aggiungere quindi codice al file di codice ThisAddIn.  Il nuovo codice usa il modello a oggetti di Word per aggiungere testo boilerplate in ogni documento salvato.  Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisAddIn`.  Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di Word.  Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  Il resto della classe `ThisAddIn` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown`.  Questi gestori eventi vengono chiamati quando Word carica e scarica il componente aggiuntivo VSTO.  Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato.  Per altre informazioni, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
#### Per aggiungere un paragrafo di testo nel documento salvato  
  
1.  Nel file di codice ThisAddIn aggiungere il codice seguente alla classe `ThisAddIn`.  Il nuovo codice definisce un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, generato quando un documento viene salvato.  
  
     Quando l'utente salva un documento, il gestore eventi aggiunge nuovo testo all'inizio del documento.  
  
     [!code-csharp[Trin_WordAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/VB/ThisAddIn.vb#1)]  
  
    > [!NOTE]  
    >  Questo codice usa il valore di indice 1 per accedere al primo paragrafo della raccolta <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>.  Anche se Visual Basic e Visual C\# usano matrici in base 0, il limite inferiore di matrice della maggior parte delle raccolte del modello a oggetti di Word è 1.  Per altre informazioni, vedere [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md).  
  
2.  Se si usa C\#, aggiungere il seguente codice obbligatorio al gestore eventi `ThisAddIn_Startup`.  Questo codice viene usato per connettere il gestore eventi `Application_DocumentBeforeSave` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  
  
     [!code-csharp[Trin_WordAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Per modificare il documento quando viene salvato, negli esempi di codice precedenti vengono usati gli oggetti seguenti:  
  
-   Il campo `Application` della classe `ThisAddIn`.  Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.Word.Application> che rappresenta l'istanza corrente di Word.  
  
-   Il parametro `Doc` del gestore eventi dell'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  Il parametro `Doc` è un oggetto <xref:Microsoft.Office.Interop.Word.Document> che rappresenta il documento salvato.  Per altre informazioni, vedere [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md).  
  
## Test del progetto  
  
#### Per sottoporre a test il progetto  
  
1.  Premere **F5** per compilare ed eseguire il progetto.  
  
     Quando si compila il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto.  Inoltre, Visual Studio crea un set di voci del Registro di sistema che consentono a Word di individuare e caricare il componente aggiuntivo VSTO e di configurare le impostazioni di sicurezza nel computer di sviluppo; in questo modo, si attiva l'esecuzione del componente aggiuntivo VSTO.  Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
2.  In Word, salvare il documento attivo.  
  
3.  Verificare che il seguente testo venga aggiunto al documento.  
  
     **Il testo è stato aggiunto tramite codice.**  
  
4.  Chiudere Word.  
  
## Pulizia del progetto  
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo.  In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si avvia Word nel computer di sviluppo.  
  
#### Per pulire il progetto completato nel computer di sviluppo  
  
1.  In Visual Studio scegliere **Pulisci soluzione** dal menu **Compila**.  
  
## Passaggi successivi  
 Ora che è stato creato un componente aggiuntivo VSTO di base per Word, è possibile acquisire altre informazioni sullo sviluppo di componenti aggiuntivi VSTO in questi argomenti:  
  
-   Attività di programmazione generali che è possibile eseguire nei componenti aggiuntivi VSTO: [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Attività di programmazione specifiche per i componenti aggiuntivi VSTO di Word: [Soluzioni Word](../vsto/word-solutions.md).  
  
-   Uso del modello a oggetti di Word: [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md).  
  
-   Personalizzazione dell'interfaccia utente di Word, ad esempio tramite l'aggiunta di una scheda personalizzata alla barra multifunzione o la creazione di un riquadro attività personalizzato: [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
-   Compilazione e debug dei componenti aggiuntivi VSTO per Word: [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione dei componenti aggiuntivi VSTO per Word: [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Vedere anche  
 [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  