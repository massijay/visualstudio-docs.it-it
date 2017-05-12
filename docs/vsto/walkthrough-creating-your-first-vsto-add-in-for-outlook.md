---
title: "Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook"
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
  - "Outlook [sviluppo per Office in Visual Studio], creazione del primo progetto"
ms.assetid: 2c5c5d75-27ee-471f-9328-58f0cf05b2b7
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per Outlook
  Questa procedura dettagliata illustra come creare un componente aggiuntivo VSTO per Microsoft Office Outlook. Le funzionalità create in questo tipo di soluzione sono disponibili per l'applicazione indipendentemente dagli elementi Outlook aperti. Per altre informazioni, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto di componente aggiuntivo VSTO per Outlook.  
  
-   Scrittura del codice che usa il modello a oggetti di Outlook per aggiungere testo all'oggetto e al corpo di un nuovo messaggio di posta elettronica.  
  
-   Creazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto completato, per fare in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Creazione del progetto  
  
#### Per creare un nuovo progetto Outlook in Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C\#** o **Visual Basic**, quindi espandere **Office\/SharePoint**.  
  
4.  Nel nodo **Office\/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office**.  
  
5.  Nell'elenco dei modelli di progetto scegliere un progetto di componente aggiuntivo VSTO di Outlook.  
  
6.  Nella casella **Nome**, digitare **FirstOutlookAddIn**.  
  
7.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di creare il progetto **FirstOutlookAddIn** e di aprire il file di codice **ThisAddIn** nell'editor.  
  
## Scrittura del codice che aggiunge testo a ogni nuovo messaggio di posta elettronica  
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di Outlook per aggiungere il testo a ciascun nuovo messaggio di posta elettronica. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisAddIn`. Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di Outlook. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md). Il resto della classe `ThisAddIn` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown`. Questi gestori eventi vengono chiamati quando Outlook carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato. Per altre informazioni, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
#### Per aggiungere testo all'oggetto e al corpo di ciascun nuovo messaggio di posta elettronica  
  
1.  Nel file di codice ThisAddIn, dichiarare un campo denominato `inspectors` nella classe `ThisAddIn`. Il campo `inspectors` gestisce un riferimento alla raccolta di finestre di controllo nell'istanza Outlook corrente. Questo riferimento impedisce al Garbage Collector di liberare la memoria in cui è contenuto il gestore eventi per l'evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>.  
  
     [!code-csharp[Trin_OutlookAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_OutlookAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Sostituire il metodo `ThisAddIn_Startup` con il codice seguente. Questo codice consente di collegare un gestore eventi all'evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>.  
  
     [!code-csharp[Trin_OutlookAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookAddInTutorial#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#2)]  
  
3.  Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn`. Questo codice consente di definire un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>.  
  
     Quando l'utente crea un nuovo messaggio di posta elettronica, questo gestore eventi consente di aggiungere il testo alla riga dell'oggetto e al corpo del messaggio.  
  
     [!code-csharp[Trin_OutlookAddInTutorial#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookAddInTutorial#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#3)]  
  
 Per modificare ciascun nuovo messaggio di posta elettronica, negli esempi di codice precedenti vengono usati gli oggetti seguenti:  
  
-   Il campo `Application` della classe `ThisAddIn`. Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.Outlook.Application> che rappresenta l'istanza corrente di Outlook.  
  
-   Il parametro `Inspector` del gestore eventi dell'evento <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>. Il parametro `Inspector` è un oggetto <xref:Microsoft.Office.Interop.Outlook.Inspector> che rappresenta la finestra di controllo del nuovo messaggio di posta elettronica. Per altre informazioni, vedere [Soluzioni Outlook](../vsto/outlook-solutions.md).  
  
## Test del progetto  
 Quando il progetto viene compilato ed eseguito, verificare che il testo venga visualizzato nella riga dell'oggetto e nel corpo di un nuovo messaggio di posta elettronica.  
  
#### Per testare il progetto  
  
1.  Premere **F5** per compilare ed eseguire il progetto.  
  
     Quando si crea il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Visual Studio crea anche un set di voci del Registro di sistema che consentono a Outlook di trovare e caricare il componente aggiuntivo VSTO e di configurare le impostazioni di sicurezza nel computer di sviluppo; in questo modo, si attiva l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Office Solution Build Process Overview](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).  
  
2.  In Outlook, creare un nuovo messaggio di posta elettronica.  
  
3.  Verificare che il testo seguente venga aggiunto sia alla riga dell'oggetto, sia al corpo del messaggio.  
  
     **This text was added by using code.**  
  
4.  Chiudere Outlook.  
  
## Pulizia del progetto  
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si apre Outlook nel computer di sviluppo.  
  
#### Per pulire il progetto  
  
1.  In Visual Studio, nel menu **Compila**, fare clic su **Pulisci soluzione**.  
  
## Passaggi successivi  
 Ora che è stato creato un componente aggiuntivo VSTO di base per Outlook, è possibile visualizzare altre informazioni sullo sviluppo di componenti aggiuntivi VSTO in questi argomenti:  
  
-   Attività di programmazione generali che è possibile eseguire usando i componenti aggiuntivi VSTO per Outlook. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Uso del modello a oggetti di Outlook. Per altre informazioni, vedere [Soluzioni Outlook](../vsto/outlook-solutions.md).  
  
-   Personalizzazione dell'interfaccia utente di Outlook, ad esempio con l'aggiunta di una scheda personalizzata alla barra multifunzione o la creazione di un riquadro attività personalizzato. Per altre informazioni, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
-   Compilazione e debug di componenti aggiuntivi VSTO per Outlook. Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione di componenti aggiuntivi VSTO per Outlook. Per altre informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Vedere anche  
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluzioni Outlook](../vsto/outlook-solutions.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  