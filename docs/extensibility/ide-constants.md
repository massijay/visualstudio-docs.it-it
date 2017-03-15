---
title: "Costanti IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Errori IDE"
  - "viste logiche"
  - "errori [Visual Studio], IDE"
  - "Costanti di contesto dell'interfaccia utente"
  - "costanti, IDE di Visual Studio"
  - "IDE, costanti"
  - "viste fisiche"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Costanti IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La <xref:Microsoft.VisualStudio.VSConstants> classe fornisce le costanti che sono specifici per l'ambiente di sviluppo integrato \(IDE\) e che sono stati definiti in precedenza solo nel file di intestazione.  
  
## Visualizzazioni logiche e fisiche  
  
|Valore|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori necessario passare questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> per ottenere il **Apri con** la finestra di dialogo, in questo caso nelle viste codice possibili.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> per ottenere il **Apri con** la finestra di dialogo, in questo caso popolata con i possibili <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> debug visualizzazioni che eseguono il mapping alla stessa vista come <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> per ottenere il **Apri con** la finestra di dialogo, in questo caso per **Visualizza modulo** visualizzazioni di progettazione.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> per ottenere il **Apri con** la finestra di dialogo, in questo caso la visualizzazione predefinita o primario della factory editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> per ottenere il **Apri con** della finestra di dialogo per una visualizzazione dell'editor di testo documento o di dati.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo che richiede all'utente di scegliere Visualizzazione definito dall'utente da utilizzare.|  
  
## Flag di Factory editor  
  
|Valore|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|Un flag obsoleto combinati bit per bit come il primo parametro di <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|Combinazione bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, metodo, indica la factory editor deve eseguire le correzioni necessarie.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|Combinazione bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(metodo\), questo flag è reciprocamente esclusivo di <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|Combinazione bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(metodo\), indica la factory editor deve creare l'editor senza visualizzare un'interfaccia utente \(UI\).|  
  
## Errori di Visual Studio  
  
|Valore|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Una costante restituita da interfacce di comportamento asincrono quando l'oggetto in questione in già occupato|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per "dati del documento incompatibili".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica "Pacchetto non è caricato."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica che il progetto esiste già."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica "configurazione del progetto non riuscita."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica "Progetto non caricato."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica "Soluzione già aperta."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica "Soluzione non aperta".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Restituito dalle interfacce di compilazione che dispongono di parametri per la specifica di una matrice di <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfaccia, ma l'implementazione sono applicabili solo il metodo per tutti gli output.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Il <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> restituisce questo valore se il documento ha un formato che non può essere aperto nell'editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valore HRESULT che indica che l'utente fare clic sul pulsante Indietro in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] procedura guidata.|  
  
## Costanti di Visual Studio  
  
|Valore|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Un errore HRESULT specifico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e che indica "Progetto inoltrato".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Costante che specifica per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per un "marcatore di casella degli strumenti".|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Costante che specifica per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per la trasmissione di un messaggio di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica l'inizio della modalità.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Costante che specifica per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per la trasmissione di un messaggio di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica la fine di modalità.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Costante che specifica per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per la trasmissione di un messaggio di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo per indicare che le metriche di barra dei comandi sono stati modificati.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Costante che specifica per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che indica che non è stato impostato un cookie.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|Oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificatore dell'elemento che rappresenta l'assenza di un elemento di progetto. Questo valore viene utilizzato quando non è stata effettuata alcuna selezione corrente.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|Oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificatore dell'elemento che rappresenta la radice di una gerarchia di progetto e viene utilizzato per identificare l'intera gerarchia anziché un singolo elemento.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|Oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificatore dell'elemento che rappresenta l'elemento attualmente selezionato o gli elementi, che possono includere la radice della gerarchia.|  
  
## IVsSelectionEvents  
 Viene descritto il componente dell'IDE è appena stato selezionato, in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> chiamare, ad esempio.  
  
|Costante|Valore|  
|--------------|------------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0x2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0x4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0x3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0x0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0x5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0x1|  
  
## VSSELELEMID  
 Costanti utilizzate per indicare un nuovo stato di selezione.  
  
|Costante|Valore|  
|--------------|------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## Costanti di finestra di dialogo Selettore componenti  
  
|Costante|Valore|  
|--------------|------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER \+ 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER \+ 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER \+ 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER \+ 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER \+ 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER \+ 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER \+ 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER \+ 1289|  
  
## Vedere anche  
 [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)