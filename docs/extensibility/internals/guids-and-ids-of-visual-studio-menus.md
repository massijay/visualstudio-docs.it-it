---
title: "GUID e ID del menu di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menu di Visual studio"
  - "gruppi di Visual studio"
  - "ID"
  - "menu esistenti"
  - "GUID"
  - "menu"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# GUID e ID del menu di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo argomento elenca i valori GUID e ID dei menu e gruppi sulla barra dei menu di Visual Studio. Questi valori sono definiti nel file. vsct che vengono installati come parte di Visual Studio SDK. Per altre informazioni, vedere [Gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Per ulteriori informazioni sulle modalità gestire gli oggetti di sviluppo integrato \(IDE\) di ambiente definiti nel file. vsct, vedere [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Il menu e i gruppi nella barra dei menu di Visual Studio utilizzano il GUID `guidSHLMainMenu`. Il menu stesso ha un ID `IDM_VS_TOOL_MAINMENU`.  
  
## Gruppi nella barra dei Menu di Visual Studio  
 Per aggiungere un menu alla barra dei menu, impostare uno di questi gruppi come elemento padre.  
  
|Raggruppa|ID|  
|---------------|--------|  
|Visualizzazione\/Modifica\/file|IDG\_VS\_MM\_FILEEDITVIEW|  
|Refactoring|IDG\_VS\_MM\_REFACTORING:|  
|Progetto|IDG\_VS\_MM\_PROJECT|  
|Compilazione|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|Formato o gli strumenti|IDG\_VS\_MM\_TOOLSADDINS|  
|Finestra\/Help\/Community|IDG\_VS\_MM\_WINDOWHELP|  
|Componenti aggiuntivi|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## Menu nella barra dei Menu di Visual Studio  
 Per aggiungere un gruppo a un menu di Visual Studio esistente, impostare una delle seguenti menu del padre. Sottomenu non sono inclusi in questo elenco.  
  
|Menu|ID|  
|----------|--------|  
|File|IDM\_VS\_MENU\_FILE|  
|Modifica|IDM\_VS\_MENU\_EDIT|  
|Visualizza|IDM\_VS\_MENU\_VIEW|  
|Refactoring|IDM\_VS\_MENU\_REFACTORING|  
|Progetto|IDM\_VS\_MENU\_PROJECT|  
|Compilazione|IDM\_VS\_MENU\_BUILD|  
|Formato|IDM\_VS\_MENU\_FORMAT|  
|Strumenti|IDM\_VS\_MENU\_TOOLS|  
|Finestra|IDM\_VS\_MENU\_WINDOW|  
|Componenti aggiuntivi|IDM\_VS\_MENU\_ADDINS|  
|Community|IDM\_VS\_MENU\_COMMUNITY|  
|?|IDM\_VS\_MENU\_HELP|  
  
## Gruppi nel menu di Visual Studio  
 Gli elenchi seguenti mostrano i gruppi che derivano direttamente dal menu nella barra dei menu di Visual Studio. Il modo più rapido per aggiungere un comando a un menu di Visual Studio è impostato uno di questi gruppi come padre. Gruppi che derivano dal sottomenu non vengono visualizzati in questa sezione.  
  
### Gruppi di Menu file  
  
|Raggruppa|ID|  
|---------------|--------|  
|Nuovo\/Apri|IDG\_VS\_FILE\_FILE|  
|Add|IDG\_VS\_FILE\_ADD|  
|Soluzione|IDG\_VS\_FILE\_SOLUTION|  
|Varie|IDG\_VS\_FILE\_MISC|  
|Save|IDG\_VS\_FILE\_SAVE|  
|Rinomina|IDG\_VS\_FILE\_RENAME|  
|Browser|IDG\_VS\_FILE\_BROWSER|  
|Print|IDG\_VS\_FILE\_PRINT|  
|Utilizzati più di recente|IDG\_VS\_FILE\_MRU|  
|Move|IDG\_VS\_FILE\_MOVE|  
|Esci|IDG\_VS\_FILE\_EXIT|  
  
### Modificare i gruppi di Menu  
  
|Raggruppa|ID|  
|---------------|--------|  
|Annullamento\/ripristino|IDG\_VS\_EDIT\_UNDOREDO|  
|Taglia\/Copia\/Incolla|IDG\_VS\_EDIT\_CUTCOPY|  
|Seleziona|IDG\_VS\_EDIT\_SELECT|  
|Istruzione GoTo|IDG\_VS\_EDIT\_GOTO|  
|Find|IDG\_VS\_EDIT\_FIND|  
|Oggetti|IDG\_VS\_EDIT\_OBJECTS|  
|Verbi OLE|IDG\_VS\_EDIT\_OLEVERBS|  
|Finestra di comando|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### Effettuare il refactoring di gruppi di Menu  
  
|Raggruppa|ID|  
|---------------|--------|  
|Common|IDG\_REFACTORING\_COMMON|  
|Avanzate|IDG\_REFACTORING\_ADVANCED|  
  
### Visualizza i gruppi di Menu  
  
|Raggruppa|ID|  
|---------------|--------|  
|Codice del modulo|IDG\_VS\_VIEW\_FORMCODE|  
|Browser|IDG\_VS\_VIEW\_BROWSER|  
|Definire le visualizzazioni|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Architettura di Windows|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|Organizzazione Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|Browser del codice|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|Sviluppo Windows|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|Barre degli strumenti|IDG\_VS\_VIEW\_TOOLBARS|  
|Simboli|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|Passare|IDG\_VS\_VIEW\_NAVIGATE|  
|Passare a piccoli|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|Visualizzatore oggetti|IDG\_VS\_VIEW\_OBJBRWSR|  
|Finestra di comando|IDG\_VS\_VIEW\_COMMANDWELL|  
|Pagine delle proprietà|IDG\_VS\_VIEW\_PROPPAGES|  
|Aggiorna|IDG\_VS\_VIEW\_REFRESH|  
  
### Gruppi di Menu progetto  
  
|Raggruppa|ID|  
|---------------|--------|  
|Varie aggiungere|IDG\_VS\_PROJ\_MISCADD|  
|Add|IDG\_VS\_PROJ\_ADD|  
|Cartella|IDG\_VS\_PROJ\_FOLDER|  
|Scarica\/ricarica|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|Reference|IDG\_VS\_PROJ\_REFERENCE|  
|Opzioni|IDG\_VS\_PROJ\_OPTIONS|  
|Impostazioni|IDG\_VS\_PROJ\_SETTINGS|  
  
### Creare gruppi di Menu  
  
|Raggruppa|ID|  
|---------------|--------|  
|Soluzione|IDG\_VS\_BUILD\_SOLUTION|  
|Selection|IDG\_VS\_BUILD\_SELECTION|  
|Ottimizzazione PGO|IDG\_VS\_PGO\_SELECTION|  
|Varie|IDG\_VS\_BUILD\_MISC|  
|Annulla|IDG\_VS\_BUILD\_CANCEL|  
  
### Gruppi di Menu Strumenti  
  
|Raggruppa|ID|  
|---------------|--------|  
|Riga di comando|IDG\_VS\_TOOLS\_CMDLINE|  
|Frammenti di codice|IDG\_VS\_TOOLS\_SNIPPETS|  
|Subset di oggetto|IDG\_VS\_TOOLS\_OBJSUBSET|  
|Opzioni|IDG\_VS\_TOOLS\_OPTIONS|  
|Altri 2|IDG\_VS\_TOOLS\_OTHER2|  
|Strumenti esterni|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|Personalizzazioni esterne|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### Gruppi di Menu finestra  
  
|Raggruppa|ID|  
|---------------|--------|  
|Nuovo|IDG\_VS\_WINDOW\_NEW|  
|Comando Chiudi Dock|IDG\_VS\_DOCKCLOSE|  
|Disattivazione di ancoraggio|IDG\_VS\_DOCKHIDE|  
|Disponi|IDG\_VS\_WINDOW\_ARRANGE|  
|Navigazione|IDG\_VS\_WINDOW\_NAVIGATION|  
|Elenco|IDG\_VS\_WINDOW\_LIST|  
  
### Gruppi di Menu della Guida in linea  
  
|Raggruppa|ID|  
|---------------|--------|  
|Esempi|IDG\_VS\_HELP\_SAMPLES|  
|Supporto|IDG\_VS\_HELP\_SUPPORT|  
|Informazioni su|IDG\_VS\_HELP\_ABOUT|  
  
## Sottomenu del menu di Visual Studio  
 Gerarchia riportata di seguito viene mostrato i sottomenu associati con i menu nella barra dei menu di Visual Studio. Poiché solo un gruppo può avere un menu come elemento padre, ogni sottomenu deve derivano da un gruppo in un menu, anziché direttamente dal menu. Per ulteriori informazioni sulla relazione tra i menu, gruppi e i sottomenu, vedere [Aggiunta di un sottomenu a un Menu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  I nomi dei menu nella barra dei menu di Visual Studio non sono separatamente illustrati in questa gerarchia perché essi possono essere dedotti dalla convenzione di denominazione per i gruppi nell'IDE, come indicato di seguito: IDG\_VS\_*nome Menu*\_*nome gruppo*.  
  
|Gruppo padre|Sottomenu|Gruppi figlio|  
|------------------|---------------|-------------------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1... 6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## Vedere anche  
 [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [I GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)