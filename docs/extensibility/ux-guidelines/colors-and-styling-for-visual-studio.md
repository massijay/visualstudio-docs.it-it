---
title: "I colori e lo stile di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# I colori e lo stile di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Utilizza colore in Visual Studio  
 In Visual Studio, colore viene utilizzato principalmente come strumento di comunicazione, non solo come effetto. Utilizza colore minima e riservarlo in situazioni in cui si desidera:  
  
-   Comunicare significato o associazione \(ad esempio, i modificatori piattaforma o linguaggio\)  
  
-   Attirare l'attenzione \(ad esempio, che indica una modifica dello stato\)  
  
-   Migliorare la leggibilità e fornire punti di riferimento per lo spostamento tra l'interfaccia utente  
  
-   Aumento delle opportunità  
  
 Sono disponibili diverse opzioni per l'assegnazione di colori per gli elementi dell'interfaccia utente in Visual Studio. In alcuni casi può essere difficile figura all'opzione, è opportuno per utilizzare, o come utilizzarlo in modo corretto. In questo argomento consentono di:  
  
1.  Comprendere i diversi servizi e sistemi utilizzati per definire i colori in Visual Studio.  
  
2.  Selezionare l'opzione corretta per un determinato elemento.  
  
3.  Utilizzare correttamente l'opzione selezionata.  
  
 **Importante:** mai come hardcoded esadecimale, RGB o colori di sistema per gli elementi dell'interfaccia utente. Utilizzo dei servizi offre una flessibilità messa a punto la tonalità. Inoltre, senza il servizio, non sarà in grado di sfruttare le funzionalità del cambio di tema di [Il servizio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
### Metodi per l'assegnazione di colori per gli elementi dell'interfaccia di Visual Studio  
 Scegliere il metodo più adatto a elementi dell'interfaccia utente.  
  
|L'interfaccia utente|Metodo|Cosa servono?|  
|--------------------------|------------|-------------------|  
|Non è stato incorporato o finestre di dialogo autonomo.|**Colori di sistema**|Nomi di sistema che consentono il sistema operativo definire il colore e aspetto degli elementi dell'interfaccia utente, ad esempio per i controlli di finestra di dialogo comuni.|  
|Si dispone di interfaccia utente personalizzata che si desidera essere coerente con l'ambiente complessivo di Visual Studio e si dispone di elementi dell'interfaccia utente che corrispondono alla categoria e un significato semantico dei token condiviso.|**Colori comuni condivisi**|I nomi dei token di colore predefiniti per elementi specifici dell'interfaccia utente esistente|  
|Un gruppo di funzionalità o di singole funzionalità e non vi è alcun colore condiviso per gli elementi simili.|**Colori personalizzati**|Colore i nomi dei token che sono specifiche di un'area e non deve essere condiviso con altri dell'interfaccia utente|  
|Si desidera consentire all'utente finale di personalizzare l'interfaccia utente o il contenuto \(ad esempio, per gli editor di testo o finestre di progettazione specifiche\).|**Personalizzazione dell'utente finale**<br /><br /> **\(Strumenti \> finestra di dialogo Opzioni\)**|Le impostazioni definite nella pagina "Tipi di carattere e colori" del **Strumenti \> Opzioni** finestra di dialogo o una pagina specializzata specifica di una funzionalità dell'interfaccia utente.|  
|Si dispone dell'interfaccia utente che ha creato in formato HTML.|**Daytona**|Consente di interfaccia utente creati in HTML per accedere al servizio di colore e tipo di carattere.|  
  
### Temi di Visual Studio  
 Visual Studio dispone di tre temi di colore diverso: blu chiaro e scuro. Rileva inoltre la modalità contrasto elevato, ovvero una combinazione di colori di sistema progettata per l'accessibilità.  
  
 Gli utenti viene richiesto di selezionare un tema durante il primo utilizzo di Visual Studio e sono in grado di passare i temi in un secondo momento visitando **Strumenti \> Opzioni \> ambiente \> Generale** e scegliere un nuovo tema dal menu a discesa "colori".  
  
 Gli utenti possono inoltre utilizzare Pannello di controllo per passare i propri sistemi intera in uno dei numerosi temi a contrasto elevato. Se un utente seleziona un tema a contrasto elevato, quindi il selettore di tema colori di Visual Studio non influisce sui colori in Visual Studio, anche se vengono salvate le modifiche al tema per quando l'utente chiude la modalità contrasto elevato. Per ulteriori informazioni sulla modalità contrasto elevato, vedere [Scelta di colori a contrasto elevato](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors).  
  
### Il servizio VSColor  
 Visual Studio fornisce un servizio di colore di ambiente, noto come servizio VSColor, che consente di associare i valori di colore degli elementi dell'interfaccia utente a una voce denominata contenente i valori di colore per ogni tema di Visual Studio. Ciò garantisce che i colori verranno automaticamente modificato per riflettere la corrente selezionato dall'utente del sistema o del tema modalità contrasto elevato. Utilizzo del servizio indica che l'implementazione di tutte le modifiche relative al tema di colore viene gestito in un'unica posizione, e se si utilizza colori condivisi comuni del servizio, l'interfaccia utente rifletterà automaticamente i nuovi temi nelle versioni future di Visual Studio.  
  
### Implementazione  
 Il codice sorgente di Visual Studio include diversi file di definizione del pacchetto che contengono elenchi di valori di colore corrispondente per ognuno di essi e i nomi dei token. Il servizio di colore legge il VSColors definiti in questi file di definizione del pacchetto. I colori vengono nel markup XAML o nel codice e quindi caricati tramite il **IVsUIShell5.GetThemedColor** metodo o un mapping DynamicResource.  
  
### Colori di sistema  
 Controlli comuni fanno riferimento i colori di sistema per impostazione predefinita. Se si desidera che l'interfaccia utente di utilizzare i colori di sistema, ad esempio quando si crea una finestra di dialogo incorporata o autonomo, non è necessario eseguire alcuna operazione.  
  
### Colori condivisi comuni nel servizio VSColor  
 Gli elementi di interfaccia devono riflettere l'ambiente di Visual Studio complessiva. Riutilizzando i colori condivisi comuni appropriate per il componente dell'interfaccia utente per la creazione, assicurarsi che l'interfaccia è coerenza con le altre interfacce di Visual Studio, che i colori verranno aggiornati automaticamente quando vengono aggiunti o aggiornati i temi.  
  
 Prima di utilizzare colori condivisi comuni, assicurarsi di comprendere come utilizzarli correttamente. Utilizzo non corretto dei colori comuni condivisi potrebbe comportare un'esperienza coerente, frustrante o confusione per gli utenti.  
  
### Colori personalizzabili dall'utente  
 Vedere: [Esposizione di colori per gli utenti finali](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
 Talvolta, potrebbe essere consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o l'area di progettazione. Personalizzabili componenti dell'interfaccia utente sono disponibili nel **tipi di carattere e colori** sezione la **Strumenti \> Opzioni** finestra di dialogo in cui gli utenti possono scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.  
  
 ![Tools &#62; Options dialog in Visual Studio](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301\-a\_ToolsOptionsDialog")  
  
 **Strumenti \> finestra di dialogo Opzioni**  
  
### Colori dell'interfaccia utente Web  
 Sta diventando più comune di creazione dei componenti dell'interfaccia utente mediante HTML in modo che possano essere utilizzati in Visual Studio Online e in Visual Studio. Interfaccia utente scritte in linguaggio HTML necessario comunque utilizzare il servizio VSColor durante l'esecuzione all'interno dell'ambiente di Visual Studio. Per informazioni su Daytona e come utilizzarlo, vedere [Daytona e interfaccia utente web](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI).  
  
##  <a name="BKMK_TheVSColorService"></a> Il servizio VSColor  
 Visual Studio fornisce un servizio di colore di ambiente, chiamato anche il servizio VSColor o il colore della shell. Questo servizio consente di associare i valori di colore degli elementi dell'interfaccia utente a un set contenente i colori per ogni tema di colori nome\-valore. Il servizio VSColor deve essere utilizzato per tutti gli elementi dell'interfaccia utente, in modo che i colori automaticamente cambiano per riflettere il tema selezionato dall'utente corrente e in modo che l'interfaccia utente associato al servizio colori ambiente verranno integrata con i nuovi temi nelle future versioni di Visual Studio.  
  
### Funzionamento del servizio  
 Il servizio colori ambiente legge che vscolors definito in pkgdef per il componente dell'interfaccia utente. Questi VSColors viene quindi fatto riferimento nel codice o markup XAML e vengono caricati tramite il **IVsUIShell5.GetThemedColor** o un mapping DynamicResource.  
  
 ![Environment color service architecture](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302\-a\_EnvironmentColorServiceArchitecture")  
  
 **Architettura del servizio colori ambiente**  
  
### Accedere al servizio  
 Esistono diversi modi per utilizza il servizio VSColor, a seconda di quale tipo di colore dei token di accesso e il tipo di codice si dispone.  
  
#### Colori di ambiente predefinite  
  
##### Dal codice nativo  
 La shell fornisce un servizio che fornisce accesso a COLORREF dei colori. L'interfaccia del servizio\/è:  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
 Nel file VSShell80.idl, l'enumerazione **\_\_VSSYSCOLOREX** ha costanti dei colori della shell. Per utilizzarla, passare come valore di indice uno dei valori di \_\_VSSYSCOLOREX enum documentati in MSDN o un indice regolare numero che il sistema di Windows API, **GetSysColor**, accetta. Questa operazione consente di ottenere il valore RGB del colore che deve essere utilizzato nel secondo parametro.  
  
 Se l'archiviazione di una penna o il pennello con un nuovo colore, è necessario AdviseBroadcastMessages \(all'esterno della shell di Visual Studio\) e ascoltare i messaggi WM\_SYSCOLORCHANGE e WM\_THEMECHANGED.  
  
```  
// To access the color service in native code, you'll make a call that resembles this: pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);  
  
```  
  
 **Nota:** valori COLORREF il restituiti da **GetVSSysColorEx\(\)** contengono solo R, G, i componenti B di un colore del tema. Se una voce di tema utilizza la trasparenza, il valore di canale alfa viene eliminato prima della restituzione. Pertanto, se il colore di ambiente di interesse deve essere utilizzata in una posizione in cui il canale di trasparenza è importante, è necessario utilizzare IVsUIShell5.GetThemedColor anziché IVsUIShell2::GetVSSysColorEx, come descritto più avanti in questo argomento.  
  
##### Dal codice gestito  
 Accedere al servizio VSColor attraverso il codice nativo è piuttosto semplice. Se si lavora tramite codice gestito, tuttavia, determinare la modalità di utilizzo del servizio può essere difficile. Con tali presupposti, ecco un frammento di codice c\# che illustra questo processo:  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e) { //getIVSUIShell2 IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2; Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2"); if (uiShell2 != null) { //get the COLORREF structure uint win32Color; uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color); //translate it to a managed Color structure Color myColor = ColorTranslator.FromWin32((int)win32Color); //use it e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100); } }  
```  
  
 Se si lavora in Visual Basic, utilizzare:  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### Dall'interfaccia utente WPF  
 È possibile associare ai colori di Visual Studio tramite valori esportati in ResourceDictionary dell'applicazione. Di seguito è riportato un esempio di utilizzo delle risorse dalla tabella dei colori, così come l'associazione ai dati di tipo di carattere ambiente XAML.  
  
```  
<Style TargetType="{x:Type Button}"> <Setter Property="TextBlock.FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter Property="TextBlock.FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" /> <Setter Property="Background" Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" /> </Style>  
```  
  
#### Le classi di supporto e metodi per il codice gestito  
 Per codice gestito, libreria Managed Package Framework della shell \(Microsoft.VisualStudio.Shell.12.0.dll\) contiene una coppia di classi helper facilitare l'utilizzo di temi colori.  
  
 I metodi helper di **Microsoft.VisualStudio.Shell.VsColors** classe MPF includere **GetThemedGDIColor\(\)** e **GetThemedWPFColor\(\)**. Questi metodi helper restituiscono il valore di colore di una voce di tema come System.Drawing.Color o System.Windows.Media.Color, per essere utilizzati in Windows Form o WPF UI.  
  
```  
IVsUIShell5 shell5; Button button = new Button(); button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey); button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey); /// <summary> /// Gets a System.Drawing.Color value from the current theme for the given color key. /// </summary> /// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param> /// <param name="themeResourceKey">The key to find the color for.</param> /// <returns>The current theme's value of the named color.</returns> public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey); // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); } private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Guid category = themeResourceKey.Category; __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush) { colorType = __THEMEDCOLORTYPE.TCT_Background; } // This call will throw an exception if the color is not found uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType); return BitConverter.GetBytes(rgbaColor); } public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey) { Validate.IsNotNull(vsUIShell, "vsUIShell"); Validate.IsNotNull(themeResourceKey, "themeResourceKey"); byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey); return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]); }  
  
```  
  
 La classe può essere utilizzata anche per ottenere gli identificatori VSCOLOR per una chiave di risorsa colore specifico di WPF, o viceversa.  
  
```  
public static string GetColorBaseKey(int vsSysColor); public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
 I metodi di **VsColors** classe query sul servizio VSColor per restituire il valore di colore ogni volta che vengono richiamati. Per ottenere un valore di colore come **System.Drawing.Color**, alternativa con prestazioni migliori, è possibile utilizzare i metodi di **Microsoft.VisualStudio.PlatformUI.VSThemeColor** \(classe\), che memorizza nella cache i valori di colore ottenuti dal servizio VSColor. La classe internamente sottoscrive gli eventi di messaggi broadcast shell e ignora il valore memorizzato nella cache quando si verifica un evento di modifica del tema. Inoltre, la classe fornisce un. Evento NET\-friendly sottoscrivere modifiche al tema. Utilizzare il **ThemeChanged** evento per aggiungere un nuovo gestore e utilizzare il **GetThemedColor\(\)** per ottenere colore i valori per il **ThemeResourceKeys** di interesse. Un codice di esempio potrebbe essere simile al seguente:  
  
```  
public MyWindowPanel() { InitializeComponent(); // Subscribe to theme changes events so we can refresh the colors VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged; RefreshColors(); } private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e) { RefreshColors(); // Also post a message to all the children so they can apply the current theme appropriately foreach (System.Windows.Forms.Control child in this.Controls) { NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero); } } private void RefreshColors() { this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey); this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey); } protected override void Dispose(bool disposing) { if (disposing) { VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged; base.Dispose(disposing);} }  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a> Scelta di colori a contrasto elevato  
  
### Panoramica  
 Windows utilizza diversi temi a livello di sistema di contrasto elevato che aumentare il contrasto del testo, sfondi e immagini, visualizzando gli elementi più distinta sullo schermo. Per motivi di accessibilità, è importante che gli elementi dell'interfaccia di Visual Studio rispondono correttamente quando gli utenti passano a un tema a contrasto elevato.  
  
 Solo un numero limitato di colori di sistema può essere utilizzato per i temi di contrasto elevato. Quando si sceglie il sistema di nomi di colori, tenere presenti i suggerimenti seguenti:  
  
1.  **Scegliere i colori di sistema che hanno lo stesso significato semantico** come l'elemento che è colorazione. Ad esempio, se si sceglie un colori a contrasto elevato per il testo all'interno di una finestra, utilizzare WindowText e non ControlText.  
  
2.  **Scegliere coppie di primo piano\/sfondo** insieme o non si sarà certi che la scelta colori funzionerà in tutti i temi di contrasto elevato.  
  
3.  **Determinare quali parti dell'interfaccia utente sono i più importanti e assicurarsi che le aree di contenuto si distinguono.** Si perderanno numerosi dettagli che normalmente verrebbero distinguere lievi differenze in tonalità di colore, pertanto l'utilizzo di colori del bordo sicuro è comune per definire le aree di contenuto, poiché non esistono varianti alcun colore per diverse aree di contenuto.  
  
### Set di colori di sistema  
 La tabella in [Blog del Team di WPF: riferimento SystemColors](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) indica il set completo di nomi di colori di sistema e le tonalità corrispondenti visualizzate in ogni tema.  
  
 Quando l'applicazione di questo limitato set di colori per l'interfaccia utente, *è previsto che si perderanno dettagli che erano presenti nei temi "normali"*. Di seguito è riportato un esempio dell'interfaccia utente di colori grigio meno evidenti che vengono utilizzati per distinguere le aree all'interno di una finestra degli strumenti. Quando viene utilizzata con la stessa finestra visualizzata in modalità contrasto elevato, si noterà che tutti gli sfondi sono la stessa tonalità e i bordi di tali aree sono indicati da solo bordo:  
  
 ![Properties window](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303\-a\_PropertiesWindow")  
  
 **Esempio di come dettagli vengono perse in caso di contrasto elevato**  
  
#### Scelta di colori del testo in un editor  
 Testo colorato viene utilizzato in un editor o in un'area di progettazione per indicare un significato, ad esempio, l'identificazione immediata dei gruppi di elementi simili. Un tema a contrasto elevato, tuttavia, non è la possibilità di distinguere tra più di tre colori di testo. WindowText, GrayText e HotTrackText sono solo colori disponibili nelle aree WindowBackground. Poiché non è possibile utilizzare più di tre colori, scegliere con attenzione le differenze più importanti che si desidera visualizzare nella modalità a contrasto elevato.  
  
 Tonalità per ciascuno dei tipi di token è consentiti in una superficie dell'editor, così come appaiono in ogni tema a contrasto elevato:  
  
 ![High Contrast editor comparison](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303\-b\_HCEditorComparison")  
  
 **Confronto di editor a contrasto elevato**  
  
 Esempi di area dell'editor del tema blu:  
  
 ![Editor in Blue theme](../../extensibility/ux-guidelines/media/030303-c_editorblue.png "030303\-c\_EditorBlue")  
  
 **Editor con tema blu**  
  
 ![Editor in High Contrast theme](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303\-d\_EditorHC1")  
  
 **Editor con tema a contrasto elevato \#1**  
  
### Modelli di utilizzo  
 Numero di elementi dell'interfaccia utente comuni già definiti colori a contrasto elevato. È possibile fare riferimento questi modelli di utilizzo quando si sceglie un sistema di nomi di colori in modo che gli elementi dell'interfaccia utente sono coerenti con componenti simili.  
  
|Colore di sistema|Utilizzo|  
|-----------------------|--------------|  
|ActiveCaption|-   IDE Active e finestra rafted glifi pulsante al passaggio del mouse e premere<br />-   Sfondo della barra del titolo per l'IDE e windows rafted<br />-   Sfondo della barra di stato predefinito|  
|ActiveCaptionText|-   IDE Active e rafted finestre di primo piano sulla barra del titolo \(testo e icone\)<br />-   Sfondo e il bordo di finestra attiva i pulsanti al passaggio del mouse e premere|  
|Controllo|-   Casella combinata, dall'elenco a discesa e ricerca controllo predefinito e disattivato in background, tra cui pulsante a discesa<br />-   Sfondo pulsante destinazione Dock<br />-   Sfondo della barra di comando<br />-   Sfondo casella degli strumenti|  
|ControlDark|-   Sfondo IDE<br />-   Separatori di barra dei menu e comandi<br />-   Bordo barra dei comandi<br />-   Menu ombreggiature<br />-   Separatore e bordo casella degli strumenti della scheda predefinita e al passaggio del mouse<br />-   Documentare anche in background di pulsante di overflow<br />-   Bordo glifo destinazione di ancoraggio|  
|ControlDarkDark|-   Finestra della scheda documento con stato non attivo e selezionato|  
|ControlLight|-   Bordo scheda Nascondi automaticamente<br />-   Casella combinata e bordo dell'elenco a discesa<br />-   Bordo e uno sfondo di destinazione di ancoraggio|  
|ControlLightLight|-   Bordo provvisorio selezionata, lo stato attivo|  
|ControlText|-   Casella combinata e icona di elenco a discesa<br />-   Testo scheda finestra deselezionata|  
|GrayText|-   Casella combinata e bordo disabilitato elenco a discesa, elenco a discesa glifo, testo e testo delle voci di menu<br />-   Testo del menu disabilitato<br />-   Testo dell'intestazione 'opzioni di ricerca' controllo di ricerca<br />-   Separatore di sezione controllo di ricerca|  
|Evidenziare|-   Tutti passare il mouse e premuto sfondi e i bordi, ad eccezione di elenco a discesa casella combinata documento e sfondo pulsante anche overflow bordo pulsante<br />-   Sfondo elemento selezionato|  
|HighlightText|-   Tutti al passaggio del mouse e premuti primi piani \(testo e icone\)<br />-   Strumento destinato agli window e document scheda finestra controllo in primo piano<br />-   Bordo barra del titolo della finestra di strumento attivo<br />-   In primo piano selezionato e specialistico scheda provvisoria<br />-   Documentare e bordo pulsante di overflow al passaggio del mouse e premere<br />-   Bordo icona selezionata|  
|HotTrack|-   Barra di scorrimento thumb sfondo e bordo premere<br />-   Icona freccia barra di scorrimento in premere|  
|InactiveCaption|-   IDE inattivi e finestra rafted glifi pulsante al passaggio del mouse<br />-   Sfondo della barra del titolo per l'IDE e windows rafted<br />-   Sfondo del controllo ricerca disabilitato|  
|InactiveCaptionText|-   IDE inattivi e in primo piano sulla barra del titolo windows rafted \(testo e icone\)<br />-   Finestra inattiva pulsanti sfondo e bordo al passaggio del mouse<br />-   Bordi e sfondo di pulsante di casella degli strumenti con stato non attivo<br />-   Primo piano di controllo di ricerca disabilitato|  
|Menu|-   Dello sfondo del menu a discesa<br />-   Segno di spunta selezionata e disabilitata in background|  
|MenuText|-   Bordo del menu a discesa<br />-   Controllo di segno di spunta<br />-   Icone di menu<br />-   Testo del menu a discesa<br />-   Bordo icona selezionata|  
|Barra di scorrimento|-   Barra di scorrimento e barra di scorrimento sulla freccia in background, tutti gli Stati|  
|Finestra|-   Sfondo scheda Nascondi automaticamente<br />-   Menu barra e sfondo scaffale dei comandi<br />-   Sfondo della scheda della finestra documento selezionato o con stato non attivo e il bordo di documento, per le schede aperte sia provvisorie<br />-   Sfondo della barra del titolo di finestra strumento con stato non attivo<br />-   Sfondo scheda casella degli strumenti, sia selezionato e deselezionato|  
|WindowFrame|-   Bordo IDE|  
|WindowText|-   In primo piano scheda Nascondi automaticamente<br />-   In primo piano scheda finestra strumento selezionato<br />-   Scheda della finestra di documento con stato non attivo e in primo piano selezionato o con stato non attivo scheda provvisoria<br />-   In primo piano predefinito di visualizzazione albero e passa il mouse sul glifo selezionato<br />-   Bordo selezionato scheda casella degli strumenti<br />-   Glifo, bordo e barra di scorrimento thumb in background|  
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a> Esposizione di colori per gli utenti finali  
  
### Panoramica  
 Talvolta potrebbe essere consentire all'utente finale di personalizzare l'interfaccia utente, ad esempio quando si crea un editor di codice o l'area di progettazione. È il modo più comune per eseguire questa operazione utilizzando il **Strumenti \> Opzioni** finestra di dialogo. A meno che non si dispone di altamente specializzati dell'interfaccia utente che richiede i controlli speciali, il modo più semplice per presentare la personalizzazione è tramite il **tipi di carattere e colori** pagina all'interno di **ambiente** sezione della finestra di dialogo. Per ogni elemento che espone per la personalizzazione, l'utente può scegliere di modificare il colore di primo piano, il colore di sfondo o entrambi.  
  
### Creazione di un pacchetto Visual Studio per i colori personalizzabili  
 Un VSPackage è possibile controllare i tipi di carattere e i colori tramite le categorie personalizzate e visualizzare gli elementi nella pagina delle proprietà di tipi di carattere e colori. Quando si utilizza questo meccanismo, è necessario implementare i package VS di [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) interfaccia e le interfacce associate.  
  
 In linea di principio, questo meccanismo può essere utilizzato per modificare tutti gli elementi di visualizzazione esistente e le categorie che li contengono. Tuttavia, e non deve essere utilizzato per modificare la categoria dell'Editor di testo o i relativi elementi visualizzati. Per ulteriori informazioni sulla categoria di Editor di testo, vedere [tipo di carattere e colore Panoramica](https://msdn.microsoft.com/en-us/library/bb165065.aspx).  
  
 Per implementare le categorie personalizzate o visualizzare gli elementi, è necessario un VSPackage:  
  
-   **Creare o identificare categorie nel Registro di sistema.** Implementazione dell'IDE del **tipi di carattere e colori** pagina delle proprietà utilizza queste informazioni per eseguire correttamente le query per il servizio supporta una determinata categoria.  
  
-   **Creare o identificare i gruppi nel Registro di sistema \(facoltativo\).** Potrebbe essere utile definire un gruppo, che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE automaticamente unisce le sottocategorie e distribuisce gli elementi all'interno del gruppo.  
  
-   **Implementare il supporto IDE.**  
  
-   **Gestire le modifiche di carattere e colori.**  
  
#### Per creare o identificare le categorie  
 Creare un tipo speciale di voce del Registro di sistema categoria \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< versione di Visual Studio \> \\FontAndColors\\ \< Category \>\]. \< category \> è il nome non localizzato della categoria.  
  
 Popolare il Registro di sistema con due valori:  
  
|Nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|Categoria|REG\_SZ|GUID|Creato da un GUID per identificare la categoria|  
|Pacchetto|REG\_SZ|GUID|Il GUID del servizio che supporta la categoria di VSPackage|  
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) per la categoria corrispondente.  
  
#### Per creare o identificare i gruppi  
 Creare un tipo speciale di voce del Registro di sistema categoria \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\ \< versione di Visual Studio \> \\FontAndColors\\ \< gruppo \>\]. \< gruppo \> è il nome localizzato del gruppo.  
  
 Popolare il Registro di sistema con due valori:  
  
|Nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|Categoria|REG\_SZ|GUID|Creato da un GUID per identificare la categoria|  
|Pacchetto|REG\_SZ|GUID|Il GUID del servizio che supporta la categoria di VSPackage|  
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** per il gruppo corrispondente.  
  
 ![IVsFontAndColorGroup](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304\-a\_FontAndColorGroup")  
  
### Per implementare il supporto IDE  
 Implementare [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx), che restituisce un [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaccia o un **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** interfaccia IDE per ogni categoria o il gruppo GUID specificato.  
  
 Per ogni categoria di supporta un VSPackage implementa un'istanza separata di [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) interfaccia.  
  
 I metodi implementati tramite [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) deve fornire l'IDE con:  
  
-   Elenchi di elementi visualizzati nella categoria  
  
-   Nomi localizzabili per elementi visualizzati  
  
-   Visualizzare le informazioni per ogni membro della categoria  
  
 **Nota:** ogni categoria deve contenere almeno un elemento di visualizzazione.  
  
 L'IDE utilizza il **T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup** interfaccia per definire un'unione di diverse categorie.  
  
 L'implementazione fornisce l'IDE con:  
  
-   Un elenco di categorie che costituiscono un gruppo specifico  
  
-   Accesso alle istanze di [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) ogni categoria all'interno del gruppo di supporto  
  
-   Nomi dei gruppi localizzabili  
  
#### Aggiornamento dell'IDE  
 L'IDE memorizza nella cache le informazioni sulle impostazioni del tipo di carattere e colore. Dopo qualsiasi modifica della configurazione di IDE carattere e colori, garantendo che la cache viene aggiornata di conseguenza, è buona norma.  
  
 Aggiornamento della cache viene eseguita tramite il [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) l'interfaccia e può essere eseguita a livello globale o solo elementi.  
  
### Gestione delle modifiche di carattere e colori  
 Per supportare correttamente la colorazione del testo che visualizza un VSPackage, il servizio colorazione supporta VSPackage deve rispondere alle modifiche apportate tramite la pagina delle proprietà di tipi di carattere e colori avviata dall'utente.  
  
 A tale scopo, è necessario un VSPackage:  
  
-   **gestire eventi generati da IDE** mediante l'implementazione di [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) interfaccia. L'IDE chiama il metodo appropriato segue le modifiche apportate dall'utente della pagina tipi di carattere e colori. Ad esempio, chiama il [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) metodo se si seleziona un nuovo tipo di carattere.  
  
 **OR**  
  
-   **polling l'IDE per modifiche**. Questo può avvenire tramite implementato dal sistema [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaccia. Sebbene principalmente per il supporto della persistenza, il [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) metodo possibile ottenere informazioni di carattere e colori per gli elementi di visualizzazione. Per ulteriori informazioni sulle impostazioni di carattere e colori, vedere l'articolo MSDN [l'accesso a carattere archiviati e le impostazioni di colore](https://msdn.microsoft.com/en-us/library/bb166382.aspx).  
  
 **Nota:** per assicurarsi che il polling risultati siano corretti, utilizzare il [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) per determinare se una cache scaricamento e aggiornamento sono necessari prima di chiamare i metodi di recupero dell'interfaccia di [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) interfaccia.  
  
#### Registrazione del carattere e colore categoria senza implementare interfacce  
 Esempio di codice riportato di seguito viene illustrato come registrare il tipo di carattere personalizzato e categoria a colori senza implementare interfacce:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window] "Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}" "Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}" "ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}" "NameID"=dword:00000064  
```  
  
 **NOTA:**  
  
-   "NameID" \= l'ID di risorsa del nome della categoria localizzata nel pacchetto  
  
-   "ToolWindowPackage" \= GUID del pacchetto  
  
-   "Category" \= "{9FF46859\-A47E\-47bf\-8AC5\-EC3DBE69D1FE}" è solo un esempio e il valore effettivo può essere un nuovo GUID fornito dal responsabile dell'implementazione.  
  
### Impostare il tipo di carattere e colore proprietà GUID di categoria  
 Nell'esempio di codice seguente viene illustrata l'impostazione di GUID di categoria.  
  
```  
// m_pView is your IVsTextView IVsTextEditorPropertyCategoryContainer spPropCatContainer = (IVsTextEditorPropertyCategoryContainer)m_pView; if (spPropCatContainer != null) { IVsTextEditorPropertyContainer spPropContainer; Guid GUID_EditPropCategory_View_MasterSettings = new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}"); hr = spPropCatContainer.GetPropertyCategory( ref GUID_EditPropCategory_View_MasterSettings, out spPropContainer); if(hr == 0) { hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory, catGUID); hr = spPropContainer.SetProperty( VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory, catGUID); } }  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a> Daytona e interfaccia utente web  
  
### Panoramica  
 "Daytona" è un set di API, strumenti e servizi che consentono all'utente di creare plug\-in con HTML, CSS e JavaScript che può essere utilizzato in una vasta gamma di host, ad esempio Visual Studio o F12. I plug\-in sono costituite da un componente portabile, che viene scritto in HTML, CSS e JavaScript, e i componenti facoltativi specifici dell'host. Ogni host Daytona può avere un proprio set di convenzioni dell'interfaccia utente, implicite o esplicite, che un plug\-in devono rispettare per essere visualizzati al suo ambiente nativo. Alcuni host, ad esempio Visual Studio, consentire agli utenti di apportare modifiche al tema"predefinito" in modo che gli aspetti visivi dell'host non possono essere destinati in modo statico durante la creazione di un foglio di stile. Questo costituisce una sfida per gli sviluppatori che creano portabile plug\-in. In questo argomento viene illustrato come creare web dell'interfaccia utente in Visual Studio con l'host Daytona in modo che supporta i temi e contrasto elevato.  
  
### Meccanismo di applicazione di temi Daytona  
 Il runtime Daytona fornisce un set di servizi che astrae le convenzioni dell'interfaccia utente e le funzionalità dei temi dell'host. Questi servizi verificare che i plug\-in di conformarsi alle aspettative dell'utente in base all'ambiente in cui in che sono ospitati visual. Questo comportamento viene fornito da tre funzionalità principali:  
  
1.  Un foglio di stile inseriti runtime \(plugin.css\) che si applica un set di regole CSS per interfaccia utente di un plug\-in modo trasparente e gli stili applicati il set predefinito di controlli HTML \(ad esempio, HTMLInputElement e HTMLButtonElement  
  
2.  Un set di token fornita dall'host che può essere utilizzato per gli elementi dell'interfaccia utente stile utilizzando i valori che sono basati su tema anziché hardcoded  
  
    1.  una sintassi dichiarativa per l'accesso a questi token con CSS  
  
    2.  un'API per accedere a livello di codice token tema da JavaScript  
  
3.  Notifica delle modifiche al tema  
  
#### Foglio di stile inseriti Runtime  
 Le coordinate di runtime Daytona con l'host per inserire uno stile di finestra automaticamente i temi di elementi dell'interfaccia utente standard di un plug\-in. Questo include lo stile per i concetti seguenti:  
  
-   Tipo di carattere ambiente  
  
-   Colori di sfondo  
  
-   Collegamenti ipertestuali  
  
-   Controlli del form \(ad esempio: \< selezionare \>, \< input \>, \< pulsante \>  
  
-   Tabelle  
  
-   Intestazioni  
  
-   Barre di scorrimento  
  
 Ciò significa che se l'interfaccia utente è costituita interamente da controlli dell'interfaccia utente HTML standard, quindi alcun intervento aggiuntivo non deve essere necessaria per rispondere correttamente alle modifiche al tema e per supportare il contrasto elevato.  
  
#### Interfaccia utente personalizzata  
 In quasi ogni caso complesso, lo standard controlli dell'interfaccia utente HTML saranno sufficiente per fornire un'esperienza completa per un plug\-in e personalizzata dell'interfaccia utente deve essere introdotte. Per supportare l'utilizzo di scelta e il colore del carattere appropriata, **token tema** deve essere utilizzato in modo dichiarativo nel CSS o in modo imperativo tramite l'API JavaScript descritto di seguito. Il runtime Daytona si occuperà di aggiornamento di fogli di stile che utilizzano questi token carico plug\-in e modifiche al tema.  
  
##### Token tema  
 Entrambi i token tema standard e specifiche degli host sono disponibili. I token standard sono inseriti dagli host e sempre disponibili. È preferibile utilizzare i token standard, laddove possibile. I token standard sono garantiti deve essere fornito da tutti gli host Daytona e usarli rende intrinsecamente più portabile il plug\-in. Il set di token standard è soggetta a modifiche, se devono essere aggiunti solo nuovi token e non deve essere rimosso. La versione di Visual Studio 2013 è documentata di seguito:  
  
|Nome del token|Descrizione|  
|--------------------|-----------------|  
|colore di sfondo del plug\-in|Il colore di sfondo predefinito per il plug\-in|  
|plug\-in di colore|Il colore di primo piano predefinito per il plug\-in|  
|plug\-in\-contextmenu\-active\-color|Il colore di selezione in primo piano predefinito per i menu di scelta rapida quando sono attive \(presentano lo stato attivo\)|  
|menu di scelta rapida di plug\-in\-colore di sfondo|Il colore di sfondo predefinito per i menu di scelta rapida|  
|colore del bordo di contextmenu plug\-in|Il colore del bordo predefinito per i menu di scelta rapida|  
|colore di contextmenu plug\-in|Il colore di primo piano predefinito per i menu di scelta rapida|  
|colore al passaggio del mouse di contextmenu plug\-in|Il colore di sfondo al passaggio del mouse per menu di scelta rapida|  
|plug\-in\-menu di scelta rapida, al passaggio del mouse\-\-colore del testo|Il colore di primo piano predefinito al passaggio del mouse per menu di scelta rapida|  
|plug\-in\-contextmenu\-icona\-casella di controllo|Il colore dell'icona casella di controllo predefinito per i menu di scelta rapida|  
|plug\-in\-contextmenu\-inattivo\-\-colore del testo|Il colore di selezione in primo piano predefinito per i menu di scelta rapida quando sono inattivi|  
|Colore separatore di contextmenu plug\-in|Colore del separatore predefinito per i menu di scelta rapida|  
|plug\-in\-font\-family|La famiglia di caratteri predefinito da utilizzare per il plug\-in|  
  
 In Visual Studio, i token del plug\-in del tipo di carattere seguenti si basano le impostazioni del carattere di ambiente:  
  
-   plug\-in\-font\-size  
  
-   plug\-in\-font\-weight  
  
-   evidenziazione di plug\-in\-colore di sfondo  
  
-   colore di evidenziazione plug\-in  
  
-   plug\-in colore inattivo  
  
 I token del plug\-in\-link seguenti vengono utilizzati per definire lo stile HTMLElements \(collegamenti ipertestuali\):  
  
-   colore del collegamento di plug\-in  
  
-   plug\-in\-\-active\-colore del collegamento  
  
-   colore al passaggio del mouse di collegamento plug\-in  
  
 Plugin.CSS stili barre di scorrimento per impostazione predefinita utilizzando i seguenti token per un migliore supporto di temi in diversi host \(in particolare, Visual Studio\):  
  
-   colore freccia di scorrimento plug\-in  
  
-   barra di scorrimento di plug\-in\-colore di sfondo  
  
-   Colore carattere di barra di scorrimento plug\-in  
  
 I seguenti token Selezione plug\-in vengono utilizzati per definire lo stile HTMLSelectElement \(elenco a discesa combobox\):  
  
-   plug\-in\-Selezionare\-opzione\-\-colore di sfondo  
  
-   plug\-in\-Selezionare\-opzione\-color  
  
-   plugin\-Select\-Option\-checked\-background\-color  
  
-   plugin\-Select\-Option\-checked\-Border\-Color  
  
-   plugin\-Select\-Option\-checked\-Foreground\-Color  
  
-   plugin\-Select\-Option\-Hover\-background\-color  
  
-   plugin\-Select\-Option\-Hover\-Border\-Color  
  
-   plugin\-Select\-Option\-Hover\-Foreground\-Color  
  
-   colore del bordo di selezione plug\-in  
  
-   Selezionare di plug\-in\-colore di sfondo  
  
-   Selezionare di plug\-in\-colore di primo piano  
  
-   plug\-in\-selezionare\-hover\-colore di sfondo  
  
-   plug\-in\-selezionare\-hover\-\-colore bordo  
  
-   plug\-in\-selezionare\-hover\-\-colore di primo piano  
  
-   colore del bordo di tabella plug\-in  
  
-   plug\-in\-tabella\-intestazione\-background\-color  
  
-   colore dell'intestazione di tabella plug\-in  
  
-   colore del bordo di textbox plug\-in  
  
-   casella di testo di plug\-in\-colore di sfondo  
  
-   plug\-in\-casella di testo\-color  
  
-   plug\-in\-casella di testo\-disabled\-colore di sfondo  
  
-   plug\-in\-casella di testo\-disabled\-\-colore bordo  
  
-   plug\-in\-casella di testo\-disabled\-color  
  
 Questi token devono essere utilizzati per *tutti* albero viste e tabelle, perché hanno impostazioni predefinite corrette impostate in diversi host per supportare i temi e contrasto elevato:  
  
-   plug\-in\-treeview\-contenuto\-background\-color  
  
-   colore del contenuto di treeview plug\-in  
  
-   plugin\-TreeView\-Content\-Inactive\-Selected\-Color  
  
-   plugin\-TreeView\-Content\-MouseOver\-background\-color  
  
-   plug\-in\-treeview\-contenuto\-mouseover\-color  
  
-   plugin\-TreeView\-Content\-Inactive\-Selected\-Color  
  
-   plugin\-TreeView\-Content\-Selected\-background\-color  
  
-   plugin\-TreeView\-Content\-Selected\-Border\-Color  
  
-   plug\-in\-treeview\-contenuto\-\-colore selezionato  
  
##### Token specifica dell'host  
 Oltre a supportare il set standard di token, gli host possono fornire i token non standard. A tale scopo, l'host di Visual Studio che consente il plug\-in specificare gli alias token tema in una sezione di Visual Studio\-specifiche del manifesto. Ad esempio:  
  
```  
"vs": { "theme_token_aliases": { "diagnostics-host-border": { "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22", "key_type": "BackgroundColor", "name": "Border" }, ... } }  
  
```  
  
 In questo esempio viene introdotto un tema token denominato "diagnostica\-host\-bordo", che è possibile fare riferimento in modo identico ai token standard indicato in precedenza. La categoria, key\_type e name vengono utilizzati per risolvere il colore mediante la **IVsFontAndColorStorage** interfaccia. In molti casi, è possibile trovare i colori appropriati \(e la categoria, key\_type e informazioni relative al nome\) in file XML che si trovano in vscommon\\themes. Lo stesso meccanismo viene utilizzato se il pacchetto introduce nuovi colori configurabili: corrisponde a key\_type, la categoria e nome per il colore che si desidera utilizzare. Gli autori di plug\-in devono tentare di utilizzare i token standard ogni volta che è possibile e utilizzare solo i token specifica dell'host sia assolutamente necessario.  
  
##### Utilizzo di token tema in CSS  
 Token tema vengono definiti tramite una sintassi di commento formattato in modo specifico. Le regole per l'analisi del token:  
  
1.  L'espressione di commento deve essere racchiuso tra parentesi quadre \(**\[\]**\).  
  
2.  Tutti gli spazi vuoti all'interno del commento, ma di fuori dell'espressione, viene ignorato.  
  
3.  L'espressione di commento deve seguire direttamente la proprietà che sostituisce.  
  
4.  Verranno rimosso gli spazi vuoti iniziali o finali all'interno dell'espressione.  
  
5.  Ogni nome token all'interno dell'espressione deve essere racchiuso tra parentesi graffe \(ad esempio, **{font\-family}** e **{colore al passaggio del mouse pulsante}**\). In caso contrario, debba essere gestito come un valore letterale.  
  
 Di seguito sono esempi di come il parser token sostituirà i valori CSS, supponendo che il **colore di sfondo del plug\-in** token presenta il valore \#000 e **plug\-in\-font\-family** token ha il valore di "Verdana".  
  
|CSS creati|CSS analizzato|Note|  
|----------------|--------------------|----------|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #000;`|Il valore predefinito viene sostituito con il valore dinamico specifica dell'host.|  
|`background-color: #fff; /*   [{plugin-background-color}]   */`|`background-color: #000;`|Lo spazio vuoto di fuori dell'espressione viene ignorato.|  
|`background-color: #fff; /*[   {plugin-background-color}   ]*/`|`background-color: #000;`|Vengono rimossi gli spazi vuoti iniziali e finali all'interno dell'espressione.|  
|`background-color: #fff; /*{plugin-background-color}*/`|`background-color: #fff;`|L'espressione non è racchiuso tra parentesi quadre e pertanto il commento viene ignorato.|  
|`background-color: #fff; /*[plugin-background-color]*/`|`background-color: plugin-background-color;`|Il token non è racchiuso tra parentesi graffe e pertanto viene considerato come un valore letterale.|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|Il commento non rispetta il valore della proprietà e pertanto viene ignorato.|  
|`background-color: #fff; /*[{plugin-background-color}]*/`|`background-color: #fff;`|*Come sopra*|  
|`/*[{plugin-background-color}]*/ background-color: #fff;`|`background-color: #fff;`|*Come sopra*|  
|`font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/`|`font-family: Verdana, sans-serif;`|Il token viene sostituito e il contenuto effettivo viene mantenuto.|  
|`background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/`|`background-image: linear-gradient(0% #000, 100% #000);`|*Come sopra*|  
  
 Se un file CSS include tema token deve essere contrassegnato dall'attributo data\-plug\-in\-theme dell'elemento di collegamento nel file HTML. Ad esempio:  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```  
  
##### Utilizzo di token del tema da JavaScript  
 Interfaccia utente personalizzata deve essere tema dal CSS, dove possibile, esistono scenari quando il valore di un tema di token deve essere accessibile a livello di codice. Ad esempio, se l'interfaccia utente personalizzata viene disegnata su un CanvasElement che non eredita lo stile CSS, o se un elemento dell'interfaccia utente è in corso in modo dinamico creato anziché fare riferimento a fogli di stile. Gli scenari abilitati tramite l'API Daytona **Plugin.Theme.getValue**. Questa funzione restituisce un valore di tema fornita dall'host quando viene specificato un nome del token.  
  
|Non applicare un tema|Con tema|  
|---------------------------|--------------|  
|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = "#ccc"; surface.fillRect(0, 0, 200, 200);`|`var surface = document.getElementById("surface").getContext("2d"); surface.fillStyle = ("plugin-background-color"); surface.fillRect(0, 0, 200, 200);`|  
|`var el = document.createElement("div"); el.style.backgroundColor = "#ccc";`|`var el = document.createElement("div"); el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");`|  
  
 Se i token vengono utilizzati da JavaScript**, deve gestire l'evento di modifica del tema per rispondere agli aggiornamenti**. Questo non è necessario per i token tema utilizzati in modo dichiarativo nel foglio di stile CSS, come il runtime Daytona si occupa di esso per il plug\-in. L'evento tema può essere gestito nel modo seguente:  
  
|Membro \(singolo gestore\)|Evento di DOM \(più gestori\)|  
|--------------------------------|-----------------------------------|  
|`Plugin.Theme.onchange = function () { // re-draw dynamic UI here }`|`Plugin.Theme.addEventListener("change", function () { // re-draw dynamic UI here });`|  
  
 In questo caso, sarebbe molto comune per richiamare **Plugin.Theme.getValue** in questi gestori, come il valore dei token di tema probabilmente modificato quando il tema modificato.  
  
##### Mapping di token standard  
 I token standard vengono mappati ai colori di ambiente e della Shell. Nell'elenco seguente fornisce una versione di che cosa sono i mapping.  
  
|Nome del token|Visual Studio mapping \(EnvironmentColors\)|  
|--------------------|-------------------------------------------------|  
|plug\-in di colore|ToolWindowTextColorKey|  
|colore di sfondo del plug\-in|ToolWindowBackgroundColorKey|  
|colore del collegamento di plug\-in|ControlLinkTextColorKey|  
|colore al passaggio del mouse di collegamento plug\-in|ControlLinkTextHoverColorKey|  
|plug\-in\-\-active\-colore del collegamento|ControlLinkTextPressedColorKey|  
|colore di evidenziazione plug\-in|HighlightTextColorKey|  
|evidenziazione di plug\-in\-colore di sfondo|HighlightColorKey|  
|plug\-in\-tabella\-intestazione\-background\-color|GridHeadingBackgroundColorKey|  
|colore dell'intestazione di tabella plug\-in|GridHeadingTextColorKey|  
|colore del bordo di tabella plug\-in|GridLineColorKey|  
|pulsante di plug\-in\-colore di sfondo|ButtonFaceColorKey|  
|plug\-in\-pulsante\-hover\-colore di sfondo|ButtonHighlightColorKey|  
|plug\-in\-pulsante\-color|ButtonTextColorKey|  
|colore del bordo di pulsante plug\-in|ButtonBorderColorKey|  
  
##### Modifiche al tema  
 Il Visual Studio host trigger plug\-in tema cambia quando un utente apporta modifiche alle seguenti impostazioni:  
  
 **Tema colori:**  
  
 ![Color theme changes](../../extensibility/ux-guidelines/media/0305-a_colortheme.png "0305\-a\_ColorTheme")  
  
 **Tema di ambiente:**  
  
 ![Environment theme changes](../../extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305\-b\_EnvironmentTheme")  
  
 **Tema del sistema operativo** \(solo quando si modifica da e verso il contrasto elevato\):  
  
 ![OS theme changes](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305\-c\_OSTheme")