---
title: "Creazione di aree di modulo di Outlook"
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
  - "MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "aree di modulo [sviluppo per Office in Visual Studio]"
  - "aree di modulo [sviluppo per Office in Visual Studio], creazione"
  - "Outlook [sviluppo per Office in Visual Studio], aree del modulo"
ms.assetid: a8005641-cc8b-4e07-8dca-294327cdc8d4
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Creazione di aree di modulo di Outlook
  È possibile usare aree del modulo per personalizzare i moduli di Microsoft Office Outlook.  Visual Studio fornisce strumenti avanzati che semplificano la progettazione, lo sviluppo e il debug delle aree del modulo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Vantaggi dell'uso delle aree del modulo](#Enhance)  
  
-   [Aggiunta di un'area del modulo di Outlook al progetto](#Adding)  
  
-   [Uso di Progettazione aree di form](#UsingFormRegionDesigner)  
  
-   [Uso di un'area del modulo progettata in Outlook](#UsingFormRegionDesignedOutlook)  
  
-   [Aggiunta di codice personalizzato a un'area del modulo](#AddingCustomCode)  
  
-   [Compilazione del progetto](#Building)  
  
-   [Debug di un'area del modulo](#Debugging)  
  
-   [Distribuzione di un'area del modulo](#Deploying)  
  
##  <a name="Enhance"></a> Vantaggi dell'uso delle aree del modulo  
 Le aree del modulo offrono numerosi miglioramenti rispetto allo sviluppo di moduli Outlook tradizionali:  
  
-   Personalizzare la pagina predefinita di qualsiasi modulo standard.  
  
-   Aggiungere fino a 12 pagine aggiuntive a qualsiasi modulo standard.  
  
-   Sostituire o migliorare un modulo standard.  
  
-   Visualizzare l'interfaccia utente personalizzata nel riquadro di lettura e nei controlli.  
  
 Per altre informazioni, vedere [Personalizzazione di pagine di form e aree del modulo](HV10038632).  
  
##  <a name="Adding"></a> Aggiunta di un'area del modulo di Outlook al progetto  
 È possibile usare la procedura guidata **Nuova area del modulo di Outlook** per progettare una nuova area del modulo o importare un'area del modulo progettata in Outlook.  È anche possibile riutilizzare un'area del modulo esistente, precedentemente usata in un altro progetto di componente aggiuntivo VSTO di Outlook.  
  
###  <a name="CreatingFormRegion"></a> Creazione di una nuova area del modulo usando la procedura guidata  
 Per creare un'area del modulo, aggiungere un elemento **area del modulo Outlook** a un progetto di componente aggiuntivo VSTO di Outlook.  Viene avviata la procedura guidata **Nuova area del modulo di Outlook**.  
  
 Usare la procedura guidata per indicare se si vuole progettare una nuova area del modulo o importare un'area del modulo progettata in Outlook.  Per altre informazioni sulla progettazione di una nuova area del modulo, vedere[Uso di Progettazione aree di form](#UsingFormRegionDesigner).  Per altre informazioni sull'uso di un'area del modulo progettata in Outlook, vedere [Importazione di un'area del modulo progettata in Outlook](#UsingFormRegionDesignedOutlook).  
  
 Usare la procedura guidata per specificare il tipo di area del modulo da creare.  La tabella seguente descrive ciascun tipo di area del modulo.  
  
|Tipo di area|Descrizione|  
|------------------|-----------------|  
|Separa|Aggiunge l'area del modulo come una nuova pagina a un modulo di Outlook.|  
|Adiacente|Aggiunge l'area del modulo alla parte inferiore della pagina predefinita di un modulo di Outlook.|  
|Sostituzione|Aggiunge l'area del modulo come una nuova pagina che sostituisce la pagina predefinita di un modulo di Outlook.|  
|Sostituzione completa|Sostituisce l'intero modulo di Outlook con l'area del modulo.|  
  
 È anche possibile usare la procedura guidata per specificare le condizioni di visualizzazione e selezionare il tipo di modulo da estendere.  Per altre informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Le selezioni effettuate nella procedura guidata influiscono sulle opzioni disponibili in altre pagine della procedura guidata.  Ad esempio, se si seleziona **Adiacente** o **Separa** nella pagina **Nuova area del modulo di Outlook**, i campi **Titolo** e **Descrizione** non saranno disponibili nella pagina **Fornire un testo descrittivo e selezionare le preferenze di visualizzazione**.  Questo avviene perché Outlook non usa questi campi quando viene visualizzata un'area del modulo adiacente o separata.  
  
#### File area del modulo  
 Quando si completa la procedura guidata **Nuova area del modulo di Outlook**, Visual Studio aggiunge automaticamente i seguenti file al progetto:  
  
-   Un file di codice dell'area del modulo.  Il nome di questo file corrisponde a quello specificato per l'elemento **area del modulo di Outlook** nella finestra di dialogo **Aggiungi nuovo elemento**.  Aggiungere a questo file il codice per gestire gli eventi dell'area del modulo.  
  
-   Un file di codice di Progettazione aree di form.  Questo file contiene il codice generato da Progettazione aree di form e non può essere modificato direttamente.  
  
-   Un file ofs \(Outlook Form Storage\).  
  
    > [!NOTE]  
    >  Questo file viene aggiunto al progetto solo se si importa un'area del modulo progettata in Outlook.  
  
#### Classe factory dell'area del modulo  
 Il file di codice dell'area del modulo contiene una classe parziale che implementa l'interfaccia <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>.  Si tratta della classe factory dell'area del modulo  che è responsabile della creazione di nuove istanze dell'area del modulo.  
  
 Tale classe è disponibile espandendo l'area **Factory area del form**.  
  
 La procedura guidata **Nuova area del modulo di Outlook** aggiunge a questa classe gli attributi che specificano il nome interno dell'area del modulo e le classi di messaggio che visualizzano l'area del modulo.  È possibile modificare manualmente questi attributi dopo che il file è stato aggiunto al progetto.  
  
 La maggior parte della classe factory dell'area del modulo è implementata nel file di Progettazione aree di form.  Tuttavia, il gestore eventi `FormRegionInitializing` è esposto nel file di codice dell'area del modulo  e può essere usato per specificare se l'area del modulo deve essere visualizzata in Outlook.  Per altre informazioni, vedere [Gestione degli eventi dell'area del modulo](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a> Aggiunta di un'area del modulo esistente al progetto  
 Un'area del modulo di Outlook di un altro progetto di Outlook può essere riutilizzata nel progetto corrente di componente aggiuntivo VSTO per Outlook con la finestra di dialogo **Aggiungi elemento esistente**.  
  
 L'area del modulo esistente deve avere un file di codice \(vb o cs\) perché non è possibile aggiungere i file ofs \(Outlook From Storage\) con la finestra di dialogo **Aggiungi elemento esistente**.  Tuttavia, è possibile creare un'area del modulo nuova importando un file ofs \(Outlook From Storage\).  Per altre informazioni, vedere [Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a> Uso di Progettazione aree di form  
 Progettazione aree di form consente di configurare il layout e l'aspetto di un'area del modulo.  È possibile trascinare i controlli gestiti nell'area di progettazione, fare doppio clic sui controlli per aprire i gestori eventi e impostare le proprietà nella finestra **Proprietà**.  
  
> [!NOTE]  
>  Le proprietà che influiscono sulla modalità di visualizzazione dell'area del modulo in Outlook sono disponibili sotto il nodo **Manifesto** nella finestra **Proprietà**.  
  
 Progettazione aree di form è disponibile solo se si seleziona **Progetta nuova area del modulo** nella pagina **Selezionare la modalità di creazione dell'area del modulo** della procedura guidata **Nuova area del modulo di Outlook**.  
  
 È possibile aprire Progettazione aree di form in tre modi diversi:  
  
-   In **Esplora soluzioni** fare doppio clic sul file di codice dell'area del modulo.  
  
-   In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file di codice dell'area del modulo, quindi scegliere **Visualizza finestra di progettazione**.  
  
-   In **Esplora soluzioni** selezionare il file di codice dell'area del modulo, quindi scegliere **Finestra di progettazione** dal menu **Visualizza**.  
  
 Progettazione aree di form supporta solo i controlli gestiti.  Non è possibile aggiungere controlli nativi di Outlook.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a> Importazione di un'area del modulo progettata in Outlook  
 Quando si progetta in Outlook, è possibile aggiungere all'area del modulo i controlli nativi di Outlook  che consentono di effettuare associazioni ai dati di Outlook in fase di progettazione.  Tuttavia, non si potrà usare in seguito Progettazione aree di form per aggiungere i controlli gestiti o modificare la progettazione dell'area del modulo.  
  
 È possibile importare aree del modulo in un progetto di componente aggiuntivo VSTO per Outlook usando la procedura guidata **Nuova area del modulo di Outlook**.  Nella pagina **Selezionare la modalità di creazione dell'area del modulo**, scegliere **Importa un file OFS \(Outlook Form Storage\)**.  Quindi, selezionare il percorso di un file ofs \(Outlook Form Storage\).  Outlook salva le aree del modulo come file ofs.  
  
 La procedura guidata **Nuova area del modulo di Outlook** copia il file ofs nella directory del progetto e aggiunge i riferimenti ai controlli al file di Progettazione aree di form.  È possibile quindi gestire gli eventi di controllo nel file di codice dell'area del modulo.  
  
 Per gestire gli eventi in un progetto Visual Basic, selezionare un evento dall'elenco dei nomi di metodo nella parte superiore dell'editor di codice.  
  
 Per gestire gli eventi in un progetto C\#, sottoscrivere gli eventi di controllo nel metodo <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>.  Per altre informazioni, vedere [Procedura: sottoscrivere e annullare la sottoscrizione di eventi &#40;Guida per programmatori C&#35;&#41;](http://msdn.microsoft.com/library/6319f39f-282c-4173-8a62-6c4657cf51cd).  
  
 È possibile modificare le proprietà dell'area del modulo nel metodo `InitializeManifest` della classe factory dell'area del modulo.  
  
> [!NOTE]  
>  Per importare un'area del modulo, è necessario lavorare a un progetto destinato alla stessa versione di Outlook installata nel computer di sviluppo.  Ad esempio, se è installato Outlook 2010, l'importazione di un'area del modulo potrà essere eseguita solo in un progetto creato con il modello di progetto **Componente aggiuntivo per Outlook 2010**.  
  
### Aggiornamento della progettazione di un'area del modulo importata  
 È possibile aggiungere, rimuovere o modificare i controlli dell'area del modulo.  Prima di eseguire queste operazioni, effettuare il backup del codice aggiunto al file di codice dell'area del modulo.  Quindi, aprire il file OFS in Outlook, modificare l'area del modulo e salvare le modifiche.  Usare la procedura guidata **Nuova area del modulo di Outlook** per importare il file OFS modificato.  È quindi possibile incollare il codice nel file di codice della nuova area del modulo.  
  
##  <a name="AddingCustomCode"></a> Aggiunta di codice personalizzato a un'area del modulo  
 Lo spazio dei nomi <xref:Microsoft.Office.Tools.Outlook> fornisce l'accesso alle classi che rappresentano l'area del modulo, all'elemento di Outlook che visualizza l'area del modulo e ad altri elementi utili.  L'elemento **area del modulo di Outlook** aggiunge automaticamente un riferimento a questo assembly nel progetto e inserisce l'istruzione **using** o **Imports** appropriata all'inizio del file di codice dell'area del modulo.  
  
 È possibile usare classi, metodi e proprietà nello spazio dei nomi Microsoft.Office.Interop.Outlook per eseguire la maggior parte delle attività di programmazione di Outlook.  Per altre informazioni sul modello a oggetti di Outlook, vedere [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md).  Per esempi di attività tipiche che si avvalgono del modello a oggetti di Outlook, vedere [Soluzioni Outlook](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a> Gestione di eventi dell'area del modulo  
 L'elemento **area del modulo di Outlook** aggiunge automaticamente al file di codice dell'area del modulo i seguenti tre gestori eventi.  
  
|Evento|Descrizione|  
|------------|-----------------|  
|FormRegionInitializing|Si verifica prima dell'inizializzazione dell'area del form.  È possibile selezionare le condizioni di questo gestore eventi per determinare se l'area del modulo deve essere visualizzata in Outlook.  Per altre informazioni, vedere [Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Si verifica dopo la creazione di un'istanza dell'area del modulo, ma prima della visualizzazione dell'area del modulo.|  
|FormRegionClosed|Si verifica prima della chiusura dell'area del modulo.|  
  
##  <a name="Building"></a> Compilazione del progetto  
 Quando si compila un progetto di componente aggiuntivo VSTO per Outlook contenente un'area del modulo, Visual Studio aggiunge le informazioni seguenti al Registro di sistema:  
  
-   Una chiave per ogni classe di messaggi associata a una o più aree del modulo.  
  
-   Una voce per ogni area del modulo e un valore associato che rappresenta il nome del componente aggiuntivo VSTO di Outlook.  
  
 Outlook usa queste informazioni per caricare le aree del modulo.  
  
##  <a name="Debugging"></a> Debug di un'area del modulo  
 È possibile eseguire il debug di un componente aggiuntivo VSTO di Outlook contenente un'area del modulo proprio come se si trattasse del debug di altri progetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  All'avvio del debugger di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Visual Studio avvia automaticamente Outlook.  
  
 Per visualizzare l'area del modulo è necessario aprire l'elemento di Outlook appropriato.  Ad esempio, se un'area del modulo adiacente viene aggiunta alla fine di un elemento di posta, aprire un elemento di posta.  
  
##  <a name="Deploying"></a> Distribuzione di un'area del modulo  
 Le aree del modulo sono distribuite automaticamente con il componente aggiuntivo VSTO di Outlook associato.  Non è quindi necessario eseguire un'attività particolare per distribuire un'area del modulo.  Per altre informazioni sulla distribuzione di componenti aggiuntivi VSTO, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Linee guida per la creazione delle aree di modulo di Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Fornisce informazioni che consentono di ottimizzare le aree del modulo ed evitare eventuali problemi.|  
|[Procedura: Aggiungere un'area del modulo a un progetto di componente aggiuntivo per Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Illustra come creare un'area del modulo per estendere un modulo standard o personalizzato di Microsoft Office Outlook usando la procedura guidata **Nuova area del modulo di Outlook**.|  
|[Associazione di un'area del modulo a una classe messaggio di Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Illustra come specificare quali elementi di Microsoft Office Outlook consentono di visualizzare un'area del modulo associando l'area del modulo alla classe di messaggio di ogni elemento.|  
|[Procedura dettagliata: progettazione di un'area del modulo di Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Mostra come progettare un'area del modulo personalizzata che viene visualizzata come una nuova pagina nella finestra di controllo di un contatto.|  
|[Procedura dettagliata: Importazione di un'area del modulo progettata in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Illustra come progettare un'area del modulo in Microsoft Office Outlook e come importare l'area del modulo in un progetto di componente aggiuntivo VSTO di Outlook con la procedura guidata **Nuova area del modulo di Outlook**.|  
|[Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)|Descrive come scrivere codice per mostrare, nascondere o modificare i controlli presenti in un'area del modulo e consentire agli utenti di eseguire il codice da altre aree del progetto usando la classe `Globals`.|  
|[Procedura: impedire la visualizzazione di un'area del modulo in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Illustra come impedire a Microsoft Office Outlook di visualizzare un'area del modulo per un particolare elemento.|  
|Illustra come accedere all'elemento di Outlook in cui viene visualizzata un'area del modulo.|  
|[Azioni personalizzate nelle aree di modulo di Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Descrive come consentire agli utenti di rispondere a un elemento di Outlook.|  
  
  