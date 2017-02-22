---
title: "Elemento menu | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, i menu"
  - "Elemento di menu (VSCT XML schema)"
ms.assetid: ce0560f3-b4c9-4ab2-a99c-d4e10f37b9e0
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce una voce di menu. Questi sono i sei tipi di menu: contesto, Menu, MenuController, MenuControllerLatched, sulla barra degli strumenti e ToolWindowToolbar.  
  
## Sintassi  
  
```  
<Menu guid=”guidMyCommandSet” id=”MyCommand” priority=”0x100” type=”button”>  
  <Parent>... </Parent>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Menu>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. GUID dell'identificatore di comando\/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando\/ID GUID.|  
|priority|Facoltativo. Un valore numerico che specifica la posizione relativa di un menu in un gruppo di menu.|  
|ToolbarPriorityInBand|Facoltativo. Un valore numerico che specifica la posizione relativa di una barra degli strumenti in una serie quando la finestra è ancorata.|  
|tipo|Facoltativo. Valore enumerato che specifica il tipo di elemento.<br /><br /> Se non è presente, il tipo predefinito è Menu.<br /><br /> Contesto<br /> Menu di scelta rapida che viene visualizzato quando un utente fa una finestra. Menu di scelta rapida presenta le caratteristiche seguenti:<br /><br /> -   Non utilizzare i campi padre e la priorità quando il menu viene visualizzato come un menu di scelta rapida.<br />-   Può essere utilizzato come un sottomenu e anche come un menu di scelta rapida. In questo caso, i campi ID gruppo sia priorità sono rispettati.<br />-   Non è sempre disponibile.<br /><br /> Menu di scelta rapida viene visualizzato solo quando vengono soddisfatte le condizioni seguenti:<br /><br /> -   Verrà visualizzata la finestra che lo ospita.<br />-   Il gestore del mouse in VSPackage rileva un pulsante destro del mouse sulla finestra e quindi chiama un metodo che gestisce il comando.<br />-   Menu di scelta rapida visualizzato quando si chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager.ShowContextMenu%2A> \(metodo\) \(l'approccio consigliato\) o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> \(metodo\).<br /><br /> Menu<br /> Fornisce un menu a discesa. Un menu a discesa ha le caratteristiche seguenti:<br /><br /> -   Rispetta l'elemento padre nella relativa definizione.<br />-   Deve avere un gruppo padre o un CommandPlacement a un gruppo.<br />-   Può essere un sottomenu in qualsiasi altro tipo di menu.<br />-   Viene visualizzato automaticamente ogni volta che viene visualizzato il menu padre.<br />-   Non richiede l'implementazione di qualsiasi codice VSPackage affinché venga visualizzato.<br /><br /> MenuController<br /> Fornisce un menu a discesa pulsante di menu combinato, che è in genere utilizzato nelle barre degli strumenti. Un menu MenuController presenta le caratteristiche seguenti:<br /><br /> -   Devono essere contenuti in un altro menu tramite CommandPlacement o padre.<br />-   Rispetta l'elemento padre nella relativa definizione.<br />-   Può essere qualsiasi tipo di menu padre.<br />-   Viene automaticamente reso disponibile ogni volta che viene visualizzato il menu padre.<br />-   È necessario il supporto a livello di codice per rendere il menu visualizzato.<br /><br /> Un comando dal menu del pulsante di divisione viene visualizzato sul pulsante di menu. Il comando visualizzato ha una delle seguenti caratteristiche:<br /><br /> -   È l'ultimo comando che è stato utilizzato il comando è ancora visualizzato e attivo.<br />-   È il primo comando visualizzato.<br /><br /> MenuControllerLatched<br /> Fornisce un menu di scelta rapida di pulsante di menu combinato per il quale un comando può essere specificato come la selezione predefinita mediante il comando come impostare un latch.<br /><br /> Un latch è un comando che è contrassegnato nel menu come selezionato, in genere mediante la visualizzazione di un segno di spunta. Un comando può essere contrassegnato come impostare un latch in caso affermativo la OLECMDF\_LATCHED flag impostato su di esso in un'implementazione di `QueryStatus` metodo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Un menu MenuControllerLatched presenta le caratteristiche seguenti:<br /><br /> -   Devono essere contenuti in un altro menu tramite un gruppo padre o CommandPlacement.<br />-   Rispetta l'elemento padre nella relativa definizione.<br />-   Può essere qualsiasi tipo di menu padre.<br />-   Viene reso disponibile ogni volta che viene visualizzato il menu padre.<br />-   È necessario il supporto a livello di codice per rendere il menu visualizzato.<br /><br /> Un comando dal menu del pulsante di divisione viene visualizzato sul pulsante di menu. Il comando visualizzato ha una delle seguenti caratteristiche:<br /><br /> -   È il primo comando visualizzato che è attivato.<br />-   È il primo comando visualizzato.<br /><br /> ToolBar<br /> Fornisce una barra degli strumenti. Una barra degli strumenti ha le caratteristiche seguenti:<br /><br /> -   Ignora l'elemento padre nella relativa definizione.<br />-   Impossibile stabilire un sottomenu di un gruppo, nemmeno utilizzando CommandPlacement.<br />-   Può sempre essere visualizzato facendo clic su **barre degli strumenti** sul **visualizzazione** menu.<br />-   Possono essere visualizzati utilizzando un [VisibilityItem](0932f551-972d-4194-84bb-426e3e4375e4Vis).<br />-   Non richiede alcun codice per la sua creazione. Per un esempio su come creare una barra degli strumenti, vedere [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md).<br /><br /> ToolWindowToolbar<br /> Fornisce una barra degli strumenti che è collegato a una finestra degli strumenti specifici, esattamente come una barra degli strumenti è collegato all'ambiente di sviluppo.<br /><br /> -   Ignora l'elemento padre nella relativa definizione.<br />-   Impossibile stabilire un sottomenu di un gruppo, nemmeno utilizzando CommandPlacement.<br />-   Viene visualizzata solo quando viene visualizzata la finestra degli strumenti che ospita la barra degli strumenti e VSPackage aggiunge in modo esplicito la barra degli strumenti alla finestra dello strumento. Questa operazione viene in genere eseguita quando la finestra degli strumenti viene creata ottenendo la proprietà dell'host della barra degli strumenti \(rappresentati dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost> interfaccia\) dal frame finestra degli strumenti e quindi chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolWindowToolbarHost.AddToolbar%2A> metodo.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Padre|Facoltativo. L'elemento padre della voce di menu.|  
|CommandFlag|Obbligatorio. Vedere [Elemento di Flag di comando](../extensibility/command-flag-element.md). I valori CommandFlag validi per un Menu sono come segue:<br /><br /> -   **AlwaysCreate**<br />-   **DefaultDocked**<br />-   **DefaultInvisible** \-questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **DontCache**<br />-   **DynamicVisibility** \-questo flag non influisce sulla visualizzazione delle barre degli strumenti.<br />-   **IconAndText**<br />-   **NoCustomize**<br />-   **NotInTBList**<br />-   **NoToolbarClose**<br />-   **TestoConsente di modificare**<br />-   **TextIsAnchorCommand**|  
|Stringhe|Obbligatorio. Vedere [Elemento di stringhe](../extensibility/strings-element.md). L'elemento figlio `ButtonText` elemento deve essere definito.|  
|Annotazione|Commento facoltativo.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento menu](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un VSPackage.|  
  
## Esempio  
  
```  
<Menu guid="cmdGuidWidgetCommands" id="menuIDEditWidget" priority="0x0002" type="Menu"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>Edit Widget</ButtonText> </Strings> </Parent> </Menu>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)