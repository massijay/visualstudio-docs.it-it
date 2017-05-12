---
title: "Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project"
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
  - "Project [sviluppo per Office in Visual Studio], creazione del primo progetto"
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], creazione del primo progetto"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Project
  Questa procedura dettagliata illustra come creare un componente aggiuntivo VSTO per Microsoft Office Project. Le funzionalità create in questo tipo di soluzione sono disponibili per l'applicazione, indipendentemente dai progetti aperti. Per altre informazioni, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un progetto di componente aggiuntivo VSTO di Project.  
  
-   Scrittura di codice che usa il modello a oggetti di Project per aggiungere un'attività a un nuovo progetto.  
  
-   Creazione ed esecuzione del progetto a scopo di test.  
  
-   Pulizia del progetto completato, per fare in modo che il componente aggiuntivo VSTO non venga più eseguito automaticamente nel computer di sviluppo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] o [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## Creazione del progetto  
  
#### Per creare un nuovo progetto in Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli, espandere **Visual C\#** o **Visual Basic**, quindi espandere **Office\/SharePoint**.  
  
4.  Nel nodo **Office\/SharePoint** espanso, selezionare il nodo **Componenti aggiuntivi di Office**.  
  
5.  Nell'elenco dei modelli di progetto selezionare **Componente aggiuntivo per Project 2010** o **Componente aggiuntivo per Project 2013**.  
  
6.  Nella casella **Nome** digitare **FirstProjectAddIn**.  
  
7.  Fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crea il progetto **FirstProjectAddIn** e apre il file di codice **ThisAddIn** nell'editor.  
  
## Scrittura di codice che aggiunge una nuova attività a un progetto  
 Aggiungere quindi codice al file di codice ThisAddIn. Il nuovo codice usa il modello a oggetti di Project per aggiungere una nuova attività a un progetto. Per impostazione predefinita, il file di codice ThisAddIn contiene il seguente codice generato:  
  
-   Una definizione parziale della classe `ThisAddIn`. Questa classe fornisce un punto di ingresso per il codice e consente di accedere al modello a oggetti di Project. Per altre informazioni, vedere [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md). Il resto della classe `ThisAddIn` viene definito in un file di codice nascosto che l'utente non deve modificare.  
  
-   I gestori eventi `ThisAddIn_Startup` e `ThisAddIn_Shutdown`. Questi gestori eventi vengono chiamati quando Project carica e scarica il componente aggiuntivo VSTO. Usare questi gestori eventi per inizializzare il componente aggiuntivo VSTO al momento del caricamento e per eseguire la pulizia delle risorse usate dal componente aggiuntivo VSTO quando viene scaricato. Per altre informazioni, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
#### Per aggiungere un'attività a un nuovo progetto  
  
1.  Nel file di codice ThisAddIn, aggiungere il codice seguente alla classe `ThisAddIn`. Questo codice definisce un gestore eventi per l'evento NewProject della classe Microsoft.Office.Interop.MSProject.Application.  
  
     Quando l'utente crea un nuovo progetto, questo gestore eventi aggiunge un'attività al progetto.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 Per modificare il progetto, in questo esempio di codice vengono usati gli oggetti seguenti:  
  
-   Il campo `Application` della classe `ThisAddIn`. Il campo `Application` restituisce un oggetto Microsoft.Office.Interop.MSProject.Application che rappresenta l'istanza corrente di Project.  
  
-   Il parametro `pj` del gestore eventi dell'evento NewProject. Il parametro `pj` è un oggetto Microsoft.Office.Interop.MSProject.Project che rappresenta il progetto. Per altre informazioni, vedere [Soluzioni Project](../vsto/project-solutions.md).  
  
1.  Se si usa C\#, aggiungere il seguente codice al gestore eventi `ThisAddIn_Startup`. Questo codice viene usato per connettere il gestore eventi `Application_Newproject` all'evento NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## Test del progetto  
 Quando si compila e si esegue il progetto, verificare che la nuova attività venga visualizzata nel progetto risultante.  
  
#### Per testare il progetto  
  
1.  Premere **F5** per compilare ed eseguire il progetto. Microsoft Project viene avviato e viene aperto automaticamente un nuovo progetto vuoto.  
  
     Quando si crea il progetto, il codice viene compilato in un assembly incluso nella cartella di output di compilazione relativa al progetto. Visual Studio crea anche un set di voci del Registro di sistema che permettono a Project di individuare e caricare il componente aggiuntivo VSTO e configura le impostazioni di sicurezza nel computer di sviluppo per consentire l'esecuzione del componente aggiuntivo VSTO. Per altre informazioni, vedere [Panoramica del processo di compilazione delle soluzioni Office](http://msdn.microsoft.com/it-it/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Verificare che nel progetto vuoto sia stata aggiunta una nuova attività.  
  
3.  Verificare che nel campo **Task Name** dell'attività sia visualizzato il testo seguente.  
  
     **This text was added by using code.**  
  
4.  Chiudere Microsoft Project.  
  
## Pulizia del progetto  
 Al termine dello sviluppo di un progetto, rimuovere l'assembly del componente aggiuntivo VSTO, le voci del Registro di sistema e le impostazioni di sicurezza dal computer di sviluppo. In caso contrario, il componente aggiuntivo VSTO verrà eseguito ogni volta che si apre Microsoft Project nel computer di sviluppo.  
  
#### Per pulire il progetto  
  
1.  In Visual Studio, nel menu **Compila**, fare clic su **Pulisci soluzione**.  
  
## Passaggi successivi  
 Dopo aver creato un componente aggiuntivo VSTO di base per Project, vedere gli argomenti seguenti per altre informazioni su come sviluppare componenti aggiuntivi VSTO:  
  
-   Attività di programmazione generali che è possibile eseguire usando i componenti aggiuntivi VSTO per Project: [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Uso del modello a oggetti di Project: [Soluzioni Project](../vsto/project-solutions.md).  
  
-   Compilazione e debug di componenti aggiuntivi VSTO per Project: [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
-   Distribuzione di componenti aggiuntivi VSTO per Project: [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Vedere anche  
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Soluzioni Project](../vsto/project-solutions.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)  
  
  