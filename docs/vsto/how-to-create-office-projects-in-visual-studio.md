---
title: "Procedura: creare progetti di Office in Visual Studio"
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
  - "VST.SelectDocWizard.Page1"
  - "VST.SelectDocWizard.Http"
  - "VST.SelectDocWizard.Extension"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], creazione di progetti"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], creazione di progetti"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], creazione"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], creazione"
  - "progetti Office [sviluppo per Office in Visual Studio]"
  - "progetti [sviluppo per Office in Visual Studio], creazione"
ms.assetid: 0037dbd8-0d2a-4766-90ea-81c819379582
caps.latest.revision: 96
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 95
---
# Procedura: creare progetti di Office in Visual Studio
  È possibile usare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per creare componenti aggiuntivi VSTO e personalizzazioni a livello di documento per le applicazioni di Microsoft Office. Per altre informazioni su questi tipi di progetti, vedere [Panoramica dello sviluppo di soluzioni Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Per creare un progetto di componente aggiuntivo VSTO  
  
1.  Nel menu **File** scegliere **Nuovo**, **Progetto**.  Se l'ambiente di sviluppo integrato \(IDE, Integrated Development Environment\) è configurato per usare le impostazioni di sviluppo di [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], scegliere **Nuovo** e quindi **Progetto** dal menu **File**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i progetti di Office hanno come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Per altre informazioni, vedere [Profilo client .NET Framework](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
2.  Nel riquadro dei modelli, nel nodo per il linguaggio che si vuole usare, espandere **Office\/SharePoint**.  
  
3.  Scegliere il nodo **Componenti aggiuntivi di Office**.  
  
4.  Nell'elenco dei modelli di progetto scegliere un modello di progetto del componente aggiuntivo VSTO.  Per un elenco di modelli di progetto del componente aggiuntivo VSTO disponibili, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Se i modelli di progetto non sono visibili quando si seleziona il nodo **Componenti aggiuntivi di Office**, assicurarsi che sia selezionata l'opzione **.NET Framework 4** o versione successiva nella casella combinata nella parte superiore della finestra di dialogo.  I modelli di progetto di Office sono visibili per entrambe le versioni di .NET Framework.  
  
5.  Nella casella **Nome** digitare un nome per il progetto.  Per impostazione predefinita, il nome del progetto viene usato anche come nome della soluzione.  
  
6.  Nella casella **Percorso** immettere il percorso in cui si vuole creare il progetto.  È possibile usare percorsi assoluti e UNC \(Universal Naming Convention\).  Non usare percorsi HTTP, FTP o di altri protocolli.  
  
     I percorsi hanno i formati seguenti:  
  
    -   \[*unità*\]:\\  
  
    -   \\\\*Server*\\*Condivisione*  
  
     Non usare i caratteri seguenti nel percorso:  
  
    -   Asterisco \(\*\)  
  
    -   Barra verticale \(|\)  
  
    -   Due punti \(:\) \(consentiti solo dopo la lettera di unità\)  
  
    -   Virgolette doppie \("\) \(nei percorsi che contengono spazi non sono necessarie le virgolette\)  
  
    -   Minore di \(\<\)  
  
    -   Maggiore di \(\>\)  
  
    -   Punto interrogativo \(?\)  
  
    -   Segno di percentuale \(%\)  
  
7.  Fare clic su **OK**.  
  
    > [!NOTE]  
    >  I progetti di componente aggiuntivo vengono sempre salvati al momento della creazione  e non possono essere creati come progetti temporanei.  Per altre informazioni sui progetti temporanei, vedere [Progetti temporanei](http://msdn.microsoft.com/it-it/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### Per creare un progetto di personalizzazione a livello di documento  
  
1.  Nel menu **File** scegliere **Nuovo**, **Progetto**.  Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual Basic, scegliere **Nuovo**, **Progetto** dal menu **File**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i progetti di Office hanno come destinazione [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Per altre informazioni, vedere [Profilo client .NET Framework](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
2.  Nel riquadro dei modelli, nel nodo per il linguaggio che si vuole usare, espandere **Office\/SharePoint**.  
  
3.  Selezionare il nodo **Componenti aggiuntivi di Office**.  
  
4.  Nell'elenco dei modelli di progetto scegliere un modello di progetto a livello di documento.  Per un elenco di modelli di progetto a livello di documento disponibili, vedere [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Se i modelli di progetto non sono visibili quando si seleziona il nodo **Componenti aggiuntivi di Office**, assicurarsi che sia selezionata l'opzione **.NET Framework 4** o versione successiva nella casella combinata nella parte superiore della finestra di dialogo.  I modelli di progetto di Office sono visibili per entrambe le versioni di .NET Framework.  
  
5.  Nella casella **Nome** digitare un nome per il progetto.  Per impostazione predefinita, questo nome viene usato anche per il documento.  Se l'IDE è configurato per usare le impostazioni di sviluppo di Visual C\# o le impostazioni di sviluppo generali, immettere anche un percorso e il nome della soluzione.  
  
    > [!NOTE]  
    >  Non è possibile usare caratteri surrogati nel percorso o nel nome del progetto.  Per informazioni sui caratteri surrogati, vedere [NIB: Unicode Support for Surrogate Pairs and Combining Character Sequences](http://msdn.microsoft.com/it-it/cba3285c-7b47-4ce8-8970-f48d6ac03e39).  Inoltre, se si prevede di distribuire la soluzione per l'uso offline, i caratteri nel nome del progetto devono rispettare le specifiche del protocollo HTTP.  
  
6.  Fare clic su **OK**.  
  
     Viene visualizzata la **Creazione guidata progetto Visual Studio Tools per Office**.  
  
7.  Selezionare **Crea un nuovo documento** se si vuole creare un nuovo documento per la soluzione oppure selezionare **Copia un documento esistente** se si vuole personalizzare un documento esistente.  
  
     Se si crea un nuovo documento, specificare il nome nella casella **Nome** e selezionare il formato del documento usando la casella **Formato**.  Per altre informazioni sui formati disponibili, vedere [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md).  
  
     Se si usa un documento esistente, specificare il relativo percorso nella casella **Percorso completo del documento esistente**.  È possibile usare percorsi assoluti e UNC.  Non usare percorsi HTTP, FTP o di altri protocolli per il documento.  
  
     I percorsi hanno i formati seguenti:  
  
    -   \[*unità*\]:\\  
  
    -   \\\\*Server*\\*Condivisione*  
  
     Non usare i caratteri seguenti nel percorso:  
  
    -   Asterisco \(\*\)  
  
    -   Barra verticale \(|\)  
  
    -   Due punti \(:\) \(consentiti solo dopo la lettera di unità\)  
  
    -   Virgolette doppie \("\) \(nei percorsi che contengono spazi non sono necessarie le virgolette\)  
  
    -   Minore di \(\<\)  
  
    -   Maggiore di \(\>\)  
  
    -   Punto interrogativo \(?\)  
  
    -   Segno di percentuale \(%\)  
  
    > [!NOTE]  
    >  Se si usa un documento esistente in un progetto di [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)], usare solo i documenti creati o convertiti in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)].  Analogamente, se si usa un documento esistente in un progetto di Word 2010, usare solo i documenti creati o convertiti in Word 2010.  Alcune funzionalità verranno disabilitate nel documento se si usa un documento creato in una versione precedente di Word.  Se si prova a scrivere codice che usa queste funzionalità, potrebbero verificarsi errori nel progetto.  Per convertire un documento, aprirlo in [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o Word 2010 e nella scheda **File** sulla barra multifunzione scegliere **Informazioni**, **Converti**.  
  
8.  Scegliere **Fine**.  
  
9. Aggiungere la cartella del progetto e le relative sottocartelle all'elenco di percorsi attendibili nel Centro protezione di Word nei casi seguenti:  
  
    -   Si sta creando un documento di Word basato su un file DOCM e il documento contiene un progetto VBA oppure ospita controlli Windows Form.  Aggiungendo la cartella del progetto all'elenco di percorsi attendibili sarà possibile assicurarsi che il documento funzioni come previsto in fase di progettazione.  
  
    -   Si sta creando un progetto di modello di Word basato su un file DOTX.  È necessario aggiungere la cartella del progetto all'elenco di percorsi attendibili in modo che sia possibile eseguire il progetto e il relativo debug.  
  
     Per altre informazioni su come aggiungere un documento ai percorsi attendibili, vedere l'articolo relativo a [creazione, rimozione o modifica di un percorso attendibile per i file](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62) nel sito Web Microsoft Office Online.  
  
## Vedere anche  
 [Panoramica dei modelli di progetto di Office](../vsto/office-project-templates-overview.md)   
 [Sviluppo collaborativo di soluzioni Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  