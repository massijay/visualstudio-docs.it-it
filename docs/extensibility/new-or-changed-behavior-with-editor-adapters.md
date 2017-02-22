---
title: "Comportamento nuovo o modificato con schede dell&#39;Editor | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - comportamento dell'adapter"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Comportamento nuovo o modificato con schede dell&#39;Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si sta aggiornando il codice che è stato scritto in versioni precedenti di editor di componenti di base di Visual Studio e si prevede di utilizzare l'editor adapter \(o gli shim\) invece di utilizzare la nuova API, è necessario considerare le seguenti differenze nel comportamento delle schede di editor per quanto riguarda l'editor di componenti di base precedente.  
  
## Funzionalità  
  
#### Utilizzando SetSite\)  
 È necessario chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> quando si creare buffer di testo, visualizzazioni di testo e codice windows prima di eseguire operazioni su di essi. Tuttavia, questo non è necessario se si utilizza il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> crearli, poiché i metodi Create \(\) del servizio stessi chiamano <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### Oggetto IVsCodeWindow hosting e IVsTextView nel proprio contenuto  
 È possibile ospitare entrambi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> i contenuti desiderati utilizzando la modalità di Win32 o WPF. Tuttavia, deve tenere presente che esistono alcune differenze nelle due modalità.  
  
##### Versioni Win32 e WPF di oggetto IVsCodeWindow  
 La finestra editor del codice è derivata da <xref:Microsoft.VisualStudio.Shell.WindowPane>, che implementa Win32 precedente <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia nonché il nuovo controllo WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfaccia. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodo per creare un ambiente di hosting basato su HWND, o <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> per creare un ambiente di hosting WPF. L'editor sottostante utilizza sempre WPF, ma è possibile creare il tipo di riquadro che soddisfi i requisiti di hosting se si intende incorporare questo riquadro direttamente nel proprio contenuto.  
  
##### Versioni Win32 e WPF di IVsTextView  
 È possibile impostare un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> in modalità Win32 o WPF.  
  
 Quando una factory editor crea una visualizzazione di testo, per impostazione predefinita è ospitato in un oggetto HWND, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> restituisce un oggetto HWND. Utilizzare questa modalità non di incorporare l'editor all'interno di un controllo WPF.  
  
 Per impostare una visualizzazione di testo alla modalità WPF, è necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> e passare <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> come un dell'inizializzazione del contrassegno nel `InitView` parametro. È possibile ottenere il <xref:System.Windows.FrameworkElement> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Modalità WPF è diverso dalla modalità di Win32 in due modi. In primo luogo, la visualizzazione di testo può essere ospitata in un contesto WPF. È possibile accedere al riquadro WPF eseguendo il cast di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> e chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Secondo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> comunque restituisce un oggetto HWND, ma questo HWND utilizzabile solo per controllare la posizione e impostare lo stato attivo su di esso. Non è necessario utilizzare HWND per rispondere a un messaggio WM\_PAINT, perché non avrà alcun effetto come l'editor consente di disegnare la finestra. HWND è presente solo per facilitare la transizione al nuovo editor di codice tramite le schede. Si consiglia vivamente di non utilizzare `VIF_NO_HWND_SUPPORT` Se il componente richiede un HWND, a causa di limitazioni in HWND restituito da `GetWindowHandle` in questa modalità.  
  
#### Passaggio di matrici come parametri nel codice nativo  
 Esistono molti metodi nell'API legacy editor che dispongono di parametri che includono una matrice e il relativo conteggio. Esempi sono:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Se si chiama questi metodi nel codice nativo, è necessario passare in un solo elemento alla volta. Se si passa in più di un elemento, la chiamata verrà rifiutata, a causa di problemi con l'implementazione di interoperabilità primario.  
  
 Il problema è più complesso con metodi come <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Ogni volta che questo metodo viene chiamato, Cancella precedente elenco di tipi di marcatore ignorati, pertanto non è possibile semplicemente chiamare questo metodo per tre volte con tre tipi di marcatore diverso. La soluzione sola consiste nel chiamare questo metodo solo nel codice gestito.  
  
#### Threading  
 È sempre necessario chiamare l'adattatore buffer dal thread dell'interfaccia utente. La scheda di buffer è un oggetto gestito, il che significa che la chiamata al suo interno dal codice gestito possono ignorare il marshalling COM e la chiamata verrà automaticamente effettuare il marshalling al thread dell'interfaccia utente.  Se si chiama l'adapter di buffer da un thread in background, è necessario utilizzare <xref:System.Windows.Threading.Dispatcher.Invoke%2A> o un metodo simile.  
  
#### Metodi LockBuffer  
 Tutti i metodi LockBuffer\(\) sono deprecati. Esempi sono:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### Eseguire il commit di eventi  
 Eseguire il commit non sono supportati. Chiamare il metodo che richiede per questi eventi, il metodo restituire un codice di errore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 Il <xref:EnvDTE.TextEditorEvents> non generato non è più su commit. Vengono invece attivati a ogni modifica di testo.  
  
#### Marcatori di testo  
 È necessario chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> oggetti quando vengono rimossi. Nelle versioni precedenti, è necessario solo rilasciare i marcatori.  
  
#### Numeri di riga  
 Per una varietà di metodi su <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, i numeri di riga corrispondono ai numeri di riga del buffer sottostante, i numeri di riga non questo fattore nella struttura e di ritorno a capo automatico, come in Visual Studio 2008.  
  
 I metodi interessati includono quanto segue \(l'elenco non è esaustivo\):  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### Struttura  
 I client di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> visualizzeranno solo le aree della struttura che sono stati aggiunti mediante <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Non visualizzerà le aree ad hoc, perché non vengono aggiunte tramite le schede dell'editor. Analogamente, questi saranno visibili ai client non aggiunte dai linguaggi \(inclusi i linguaggi c\# e C\+\+\) che utilizzano il nuovo editor di codice piuttosto che le schede dell'editor di aree della struttura.  
  
#### Altezza riga  
 Nell'editor di nuovo, le righe di testo possono avere altezza differente, a seconda della dimensione del carattere e le trasformazioni di riga possibili che possono spostare la riga relativa alle altre linee. L'altezza della riga restituita dai metodi, ad esempio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> è l'altezza di una riga con la dimensione predefinita applicate alcuna trasformazione di riga. Questa impostazione potrebbe o potrebbe non riflettere l'altezza effettiva di una riga nella visualizzazione.  
  
#### Gestione degli eventi e annullamento  
 Nell'editor di nuovo, la visualizzazione continua a eseguire operazioni quali il rendering e la generazione di eventi in modo continuo, anche quando è aperto un cluster di annullamento. Questo comportamento è diverso da quello delle visualizzazioni legacy, che non ha eseguito le operazioni fino a dopo la chiusura del cluster di annullamento.  
  
#### IntelliSense  
  
-   Il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> metodo avrà esito negativo se viene passato in una classe che implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. I popup proprietario Win32 personalizzati non sono più supportati.  
  
#### Smart tag  
 Non è supportata per gli smart tag creati con adapter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> le interfacce.  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> non è implementata.  
  
## Non implementati  
 Alcuni metodi non sono state implementate sulla scheda buffer di testo, adattatore di visualizzazione di testo e adapter livello testo.  
  
|Interfaccia|Non implementato|  
|-----------------|----------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` non è implementata.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> viene implementato in schede ma ignorato dall'interfaccia utente della struttura.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> viene implementato in schede ma ignorato dall'interfaccia utente della struttura.|