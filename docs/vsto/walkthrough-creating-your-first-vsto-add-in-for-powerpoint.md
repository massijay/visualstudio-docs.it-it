---
title: "Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per PowerPoint | Microsoft Docs"
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
  - "PowerPoint [sviluppo per Office in Visual Studio], creazione del primo progetto"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura dettagliata: Creazione del primo componente aggiuntivo VSTO per PowerPoint
  Questa procedura dettagliata illustra come creare un componente aggiuntivo VSTO per Microsoft Office PowerPoint.  Le funzionalità create dall'utente in questo tipo di soluzione sono disponibili per l'applicazione stessa, indipendentemente da quali presentazioni siano aperte.  Per altre informazioni, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto del componente aggiuntivo VSTO PowerPoint per PowerPoint.  
  
-   Scrittura di codice che usa il modello a oggetti di PowerPoint per aggiungere una casella di testo a ogni nuova diapositiva.  
  
-   Compilazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto, in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## Creazione del progetto  
  
#### Per creare un nuovo progetto  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C\#** o **Visual Basic**, quindi espandere **Office\/SharePoint**.  
  
4.  Nel nodo **Office\/SharePoint** espanso selezionare il nodo **Componenti aggiuntivi di Office**.  
  
5.  Nell'elenco dei modelli di progetto scegliere un progetto del componente aggiuntivo VSTO di PowerPoint.  
  
6.  Nella casella **Nome** digitare **FirstPowerPointAddIn**.  
  
7.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto **FirstPowerPointAddIn** e apre il codice **ThisAddIn** nell'editor.  
  
## Scrittura del codice che aggiunge testo a ogni nuova diapositiva  
 Aggiungere quindi codice al file di codice ThisAddIn.  Il nuovo codice usa il modello a oggetti di PowerPoint per aggiungere una casella di testo a ogni nuova diapositiva.  Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisAddIn`.  Questa classe fornisce un punto di ingresso per il codice e fornisce l'accesso al modello a oggetti di PowerPoint.  Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  Il resto della classe `ThisAddIn` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown`.  Questi gestori eventi vengono chiamati quando PowerPoint carica e scarica il componente aggiuntivo VSTO.  Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato.  Per altre informazioni, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
#### Per aggiungere una casella di testo a ogni nuova diapositiva  
  
1.  Nel file di codice ThisAddIn aggiungere il codice seguente alla classe `ThisAddIn`.  Questo codice definisce un gestore eventi per l'evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> dell'oggetto <xref:Microsoft.Office.Interop.PowerPoint.Application>.  
  
     Quando l'utente aggiunge una nuova diapositiva alla presentazione attiva, il gestore eventi aggiunge una casella di testo nella parte superiore della nuova diapositiva, quindi aggiunge il testo nella casella di testo.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Se si usa C\#, aggiungere il seguente codice al gestore eventi `ThisAddIn_Startup`.  Questo codice è necessario per connettere il gestore eventi `Application_PresentationNewSlide` all'evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Per modificare tutte le nuove diapositive, negli esempi di codice precedenti vengono usati i seguenti oggetti:  
  
-   Il campo `Application` della classe `ThisAddIn`.  Il campo `Application` restituisce un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Application> che rappresenta l'istanza corrente di PowerPoint.  
  
-   Il parametro `Sld` del gestore eventi dell'evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  Il parametro `Sld` è un oggetto <xref:Microsoft.Office.Interop.PowerPoint.Slide> che rappresenta la nuova diapositiva.  Per altre informazioni, vedere [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md).  
  
## Test del progetto  
 Quando si compila e si esegue il progetto, verificare che la casella di testo venga visualizzata nelle nuove diapositive aggiunte a una presentazione.  
  
#### Per sottoporre a test il progetto  
  
1.  Premere **F5** per compilare ed eseguire il progetto.  
  
     Quando si compila il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto.  Inoltre, Visual Studio crea un set di voci del Registro di sistema che consentono a PowerPoint di individuare e caricare il componente aggiuntivo VSTO e di configurare le impostazioni di sicurezza nel computer di sviluppo per attivare l'esecuzione del componente aggiuntivo VSTO.  Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
2.  In PowerPoint, aggiungere una nuova diapositiva alla presentazione attiva.  
  
3.  Verificare che il seguente testo venga aggiunto a una nuova casella di testo nella parte superiore della diapositiva.  
  
     **Il testo è stato aggiunto tramite codice.**  
  
4.  Chiudere PowerPoint.  
  
## Pulizia del progetto  
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo.  In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si apre PowerPoint nel computer di sviluppo.  
  
#### Per pulire il progetto  
  
1.  In Visual Studio scegliere **Pulisci soluzione** dal menu **Compila**.  
  
## Passaggi successivi  
 Ora che è stato creato un componente aggiuntivo VSTO di base per PowerPoint, è possibile ottenere altre informazioni sullo sviluppo di componenti aggiuntivi VSTO in questi argomenti:  
  
-   Attività di programmazione generali che è possibile eseguire usando i componenti aggiuntivi VSTO per PowerPoint.  Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Uso del modello a oggetti di PowerPoint.  Per altre informazioni, vedere [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Personalizzazione dell'interfaccia utente di PowerPoint, ad esempio tramite l'aggiunta di una scheda personalizzata alla barra multifunzione o la creazione di un riquadro attività personalizzato.  Per altre informazioni, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
-   Compilazione e debug di componenti aggiuntivi VSTO per PowerPoint.  Per altre informazioni, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione di componenti aggiuntivi VSTO per PowerPoint.  Per altre informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Vedere anche  
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluzioni PowerPoint](../vsto/powerpoint-solutions.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  