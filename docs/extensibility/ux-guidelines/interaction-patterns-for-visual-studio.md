---
title: "Modelli di interazione per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Modelli di interazione per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Panoramica  
 Un modello di progettazione, in generale, è alla base di una progettazione che può essere applicata in situazioni specifiche per risolvere i problemi con set simili di vincoli. Finestre di progettazione di funzionalità e di sistema utilizzare modelli di progetto come punti, che possono essere adattati alle loro esigenze di partenza.  
  
 Visual Studio include una libreria dei modelli di interazione comuni che devono essere considerati durante la creazione di nuove funzionalità. Esistono due contesti di base per i modelli di progettazione: Client \(devenv\) di Visual Studio e Visual Studio Online. Per alcuni problemi di progettazione, è disponibile un modello diffuso che funziona bene in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente che viene presentato all'interno di un browser e di cui è ospitato in un'applicazione client.  
  
### Tipi di modello di Visual Studio Client  
  
|Tipo di modello|Descrizione|Esempi|  
|---------------------|-----------------|------------|  
|**Modelli a livello di applicazione**|Modelli di alto livello comuni all'applicazione, determinazione o la visualizzazione di contesto dell'applicazione e contenente composita e pattern di controllo al loro interno|-   Finestre degli strumenti<br />-   Finestre di documento|  
|**Modelli compositi**|Modelli comuni che possono estendersi tra modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distinto|-   Cambio di visualizzazione<br />-   Generatori di elenco<br />-   Visualizzazione di dati<br />-   Notifiche<br />-   Convalida<br />-   Modelli di selezione|  
|**Pattern di controllo**|Informazioni specifiche sui controlli di basso livello come previsto si comportino|-   Visualizzazioni ad albero<br />-   La modifica all'interno di un controllo griglia|  
  
## Modelli di applicazione  
 In generale, l'interfaccia di Visual Studio comprende più finestre, finestre di dialogo, comandi e barre degli strumenti all'interno di un unico IDE. Gerarchia di Visual Studio determina i menu di contesto e le unità. I punti di integrazione principali nell'interfaccia utente dell'IDE sono finestre di documento finestre degli strumenti, progetti, la struttura di comando, l'editor di testo, casella degli strumenti, la finestra proprietà e gli strumenti \> Opzioni.  
  
 Sono disponibili modelli di utilizzo di base per ognuno dei punti di integrazione principali nell'interfaccia utente dell'IDE:  
  
-   [Menu e comandi di Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Modelli di applicazione per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interazioni di finestra](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenzioni di editor](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## Pattern di controllo comune  
 Pattern di controllo sono principalmente sui come singoli controlli sono previsti un comportamento. Si tratta di un'area in cui è più importante garantire uniformità.  
  
 Controlli più comuni in Visual Studio devono seguire le linee guida di Windows Desktop. Linee guida include solo le aree in cui è necessario aumentare le convenzioni comuni con interazioni specifici di Visual Studio o luoghi in cui si sostituiscono le linee guida interamente per personalizzare Visual Studio per soddisfare le esigenze dei nostri utenti sofisticati.  
  
-   [Pattern di controllo comune per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## Modelli compositi  
 Esistono diversi modi che gli utenti si aspettano per eseguire attività. Laddove possibile, le funzionalità devono essere progettate per utilizzare tali modelli per l'interazione e progettazione visiva.  
  
 Sebbene esistano numerosi modelli compositi all'interno di Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:  
  
-   [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Per gli oggetti dell'interfaccia utente e la lettura](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistenza e il salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)