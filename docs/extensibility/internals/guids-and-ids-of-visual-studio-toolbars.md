---
title: "GUID e ID delle barre degli strumenti di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gruppi di Visual studio"
  - "barre degli strumenti"
  - "barra degli strumenti di Visual studio"
  - "ID"
  - "gruppo toolgar"
  - "finestra degli strumenti"
  - "GUID"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# GUID e ID delle barre degli strumenti di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo argomento enumera i valori ID e di GUID delle barre degli strumenti inclusi nell'ambiente di sviluppo integrato di \(IDE\) Visual Studio e gruppi contengono.  Questi valori sono definiti in file di .vsct installati come parte di Visual Studio SDK.  Per ulteriori informazioni, vedere [Gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Molte delle barre degli strumenti disponibili in Visual Studio non sono definite da Visual Studio e i relativi valori ID e di GUID non sono pubblici.  In questo argomento vengono elencati solo le barre degli strumenti definite nei file di Visual Studio SDK .vsct.  
  
 Per ulteriori informazioni su come utilizzare gli oggetti dell'IDE definiti in file di .vsct, vedere [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Le barre degli strumenti predefinite fornite dall'IDE di Visual Studio utilizzano il GUID `guidSHLMainMenu`, a eccezione di quanto specificato in caso contrario mediante GUID: sintassi di ID.  
  
## IDE Toolbars  
 Le barre degli strumenti sono fornite dall'IDE di Visual Studio.  Le barre degli strumenti è possibile visualizzare selezionandoli dal sottomenu di **Barre degli strumenti** del menu di **strumenti** .  Le barre degli strumenti in finestre degli strumenti non sono inclusi in questa sezione.  
  
 Solo i gruppi possono discendere direttamente dalle barre degli strumenti.  Per aggiungere un gruppo, impostare il padre al GUID e sull'ID della barra degli strumenti.  Per aggiungere un pulsante in una barra degli strumenti, impostare il padre a un gruppo della barra degli strumenti.  
  
|Barra degli strumenti|ID|  
|---------------------------|--------|  
|Standard|IDM\_VS\_TOOL\_STANDARD|  
|Compila|IDM\_VS\_TOOL\_BUILD|  
|Editor di testo|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Debug|guidVSDebugGroup: IDM\_DEBUG\_TOOLBAR|  
|percorso di debug|guidVSDebugGroup: IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### Barre degli strumenti speciali  
 Le barre degli strumenti sono definite dall'IDE di Visual Studio, ma risponde alle funzioni e specializzate non ospitano i gruppi di controlli.  
  
|Barra degli strumenti|ID|  
|---------------------------|--------|  
|aggiungere il comando|IDM\_VS\_TOOL\_ADDCOMMAND|  
|Non definito|IDM\_VS\_TOOL\_UNDEFINED|  
|XML Schema|IDM\_VS\_TOOL\_SCHEMA|  
|Dati XML|IDM\_VS\_TOOL\_DATA|  
  
## Gruppi sulle barre degli strumenti dell'IDE  
 Per aggiungere un pulsante in una barra degli strumenti standard, impostare uno dei seguenti gruppi come relativo padre.  I gruppi vengono ordinati in base alla barra degli strumenti padre.  
  
### Gruppi la barra degli strumenti standard  
  
|Nome|ID|  
|----------|--------|  
|Salvare e aprire|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|Taglia e copia|IDG\_VS\_TOOLSB\_CUTCOPY|  
|Fase di annulla\/ripristina|IDG\_VS\_TOOLSB\_UNDOREDO|  
|Esecuzione\/compilazione|IDG\_VS\_TOOLSB\_RUNBUILD|  
|Cerca|IDG\_VS\_TOOLSB\_SEARCH|  
|Windows|IDG\_VS\_TOOLSB\_WINDOWS|  
|nuove finestre|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|Caricamento e salvataggio|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|contatore|IDG\_VS\_TOOLSB\_GAUGE|  
  
### Gruppi della barra degli strumenti di compilazione  
  
|Nome|ID|  
|----------|--------|  
|Barra di compilazione|IDG\_VS\_BUILDBAR|  
|Cancel|IDG\_VS\_BUILD\_CANCEL|  
  
### Gruppi della barra degli strumenti editor di testo  
  
|Nome|ID|  
|----------|--------|  
|Completamento|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Indent|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|Commento|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|Segnalibri|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### Gruppi della barra degli strumenti di Debug  
  
|Nome|ID|  
|----------|--------|  
|Esecuzione|IDM\_DEBUG\_TOOLBAR|  
|Esecuzione di istruzioni|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|Windows|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### Gruppi della barra degli strumenti posizione di debug  
  
|Nome|ID|  
|----------|--------|  
|percorso di debug|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## Barre degli strumenti della finestra degli strumenti  
 Le barre degli strumenti possono essere visualizzati direttamente nell'IDE o nelle finestre degli strumenti come **Esplora soluzioni**.  Poiché le finestre degli strumenti non sono definite nei file di .vsct, le barre degli strumenti della finestra degli strumenti non hanno padre definiti.  Al contrario, vengono inseriti nel codice.  Nella tabella seguente sono illustrate le barre degli strumenti visualizzate nelle finestre degli strumenti nell'IDE e gruppi di controlli che contengono.  
  
> [!NOTE]
>  Le barre degli strumenti e i gruppi utilizzano il GUID `guidSHLMainMenu`, a eccezione di quanto specificato in caso contrario mediante GUID: sintassi di ID.  Dove un GUID è specificato per una barra degli strumenti, si applica ai gruppi che discendono dalla barra degli strumenti.  
  
|Finestra degli strumenti|Barra degli strumenti|Groups|  
|------------------------------|---------------------------|------------|  
|Esplora soluzioni|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|Esplora server|guid\_SE\_MenuGroup: IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|Proprietà|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|Visualizzazione classi|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|Visualizzazione classi|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEAR CH2|  
|Visualizzatore oggetti|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|Visualizzatore oggetti|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEAR CH2|  
|Output|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|Trova e sostituisci|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|Risultati 1 di ricerca|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|Risultati 2 di ricerca|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|Segnalibri|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|Elenco attività|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|Attività dell'utente|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|Elenco errori|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|Visualizzatore chiamate|IDM\_VS\_TOOL\_ CALLBROWSER1. .16|\_ACTIONS OF IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_TYPE OF IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_CBSETTINGS OF IDG\_VS\_TOOLBAR\_ CALLBROWSER1|  
|Punti di interruzione|guidVSDebugGroup: IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|disassembly|guidVSDebugGroup: IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|memoria 1\-4|guidVSDebugGroup: IDM\_MEMORY\_WINDOW\_TOOLBAR1… 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_ COLUMNS1. .4|  
|Processi|guidVSDebugGroup: IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXE CCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## Vedere anche  
 [Aggiunta di un Controller di Menu per una barra degli strumenti](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUID e ID del menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)