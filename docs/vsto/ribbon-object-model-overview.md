---
title: "Cenni preliminari sul modello a oggetti della barra multifunzione"
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
  - "barra multifunzione [sviluppo per Office in Visual Studio], modello a oggetti"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Cenni preliminari sul modello a oggetti della barra multifunzione
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] espone un modello a oggetti fortemente tipizzato per ottenere e impostare le proprietà della barra multifunzione in fase di esecuzione.  Ad esempio, è possibile popolare dinamicamente i controlli dei menu oppure attivare o disattivare la visualizzazione dei controlli in base al contesto.  È inoltre possibile aggiungere schede, gruppi e controlli a una barra multifunzione, ma solo prima della barra multifunzione viene caricato dall'applicazione di Office.  Per informazioni, vedere [Impostazione di proprietà che diventano di sola lettura](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Questo modello a oggetti della barra multifunzione è costituito principalmente dalla [classe Ribbon](#RibbonClass), dagli [eventi della barra multifunzione](#RibbonEvents) e dalle [classi di controlli della barra multifunzione](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Classe Ribbon  
 Quando si aggiunge un nuovo elemento **Barra multifunzione \(finestra di progettazione visiva\)** a un progetto, Visual Studio aggiunge una classe **Ribbon** al progetto.  La classe **Ribbon** eredita dalla classe <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>.  
  
 Questa classe viene visualizzata come classe parziale suddivisa tra il file di codice della barra multifunzione e il file di codice della finestra di progettazione della barra multifunzione.  
  
##  <a name="RibbonEvents"></a> Eventi della barra multifunzione  
 La classe **Ribbon** contiene i tre eventi seguenti:  
  
|Evento|Descrizione|  
|------------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Generato quando l'applicazione di Office carica la personalizzazione della barra multifunzione.  Il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> viene aggiunto automaticamente al file di codice della barra multifunzione.  Utilizzare questo gestore eventi per eseguire il codice personalizzato al caricamento della barra multifunzione.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Consente di memorizzare le immagini della personalizzazione della barra multifunzione al caricamento della barra multifunzione.  È possibile ottenere un lieve miglioramento delle prestazioni se si scrive codice per memorizzare le immagini della barra multifunzione in questo gestore eventi.  Per ulteriori informazioni, vedere <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Generato quando l'istanza della barra multifunzione viene chiusa.|  
  
##  <a name="RibbonControlClasses"></a> Controlli della barra multifunzione  
 Lo spazio dei nomi <xref:Microsoft.Office.Tools.Ribbon> contiene un tipo per ogni controllo presente nel gruppo **Controlli barra multifunzione di Office** della **Casella degli strumenti**.  
  
 La tabella seguente sono indicati il tipo per ogni controllo `Ribbon`.  Per la descrizione di ciascun controllo, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
|Nome del controllo|Nome di classe|  
|------------------------|--------------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Raggruppare**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Etichetta**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separatore**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 Lo spazio dei nomi <xref:Microsoft.Office.Tools.Ribbon> utilizza il prefisso "Ribbon" per questi tipi al fine di evitare conflitti con i nomi delle classi di controllo nello spazio dei nomi <xref:System.Windows.Forms>.  
  
 Quando si aggiunge un controllo alla finestra di progettazione della barra multifunzione, questa dichiara la classe per il controllo come un campo nel file di codice della finestra di progettazione della barra multifunzione.  
  
### Attività comuni mediante le proprietà dei controlli della barra multifunzione  
 Ogni controllo `Ribbon` contiene proprietà che è possibile utilizzare per eseguire varie attività, come l'assegnazione di un'etichetta a un controllo, o nascondere e mostrare i controlli.  
  
 In alcuni casi, le proprietà diventano di sola lettura dopo il caricamento della barra multifunzione o dopo l'aggiunta di un controllo a un menu dinamico.  Per ulteriori informazioni, vedere [Impostazione di proprietà che diventano di sola lettura](#SettingReadOnlyProperties).  
  
 Nella tabella seguente vengono descritte alcune attività che è possibile eseguire utilizzando le proprietà del controllo `Ribbon`.  
  
|Per questa attività:|Eseguire questa operazione:|  
|--------------------------|---------------------------------|  
|Attivare o disattivare la visualizzazione di un controllo.|Utilizzare la proprietà Visible.|  
|Abilitare o disabilitare un controllo.|Utilizzare la proprietà Enabled.|  
|Impostare le dimensioni di un controllo.|Utilizzare la proprietà ControlSize.|  
|Ottenere l'immagine che viene visualizzata in un controllo.|Utilizzare la proprietà Image.|  
|Modificare l'etichetta di un controllo.|Utilizzare la proprietà Label.|  
|Aggiungere dati definiti dall'utente a un controllo.|Utilizzare la proprietà Tag.|  
|Ottenere gli elementi in un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.|Utilizzare la proprietà Items.|  
|Aggiungere elementi a un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilizzare la proprietà Items.|  
|Aggiungere i controlli a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Utilizzare la proprietà Items.<br /><br /> Per aggiungere controlli a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> dopo il caricamento della barra multifunzione nell'applicazione di Office, è necessario impostare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> a **true** prima del caricamento della barra multifunzione nell'applicazione di Office.  Per informazioni, vedere [Impostazione di proprietà che diventano di sola lettura](#SettingReadOnlyProperties).|  
|Ottenere l'elemento selezionato di un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilizzare la proprietà SelectedItem.  Per un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, utilizzare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>.|  
|Ottenere i gruppi in un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Utilizzare la proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Specificare il numero di righe e colonne che vengono visualizzate in un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilizzare le proprietà <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>.|  
  
##  <a name="SettingReadOnlyProperties"></a> Impostazione di proprietà che diventano di sola lettura  
 Alcune proprietà possono essere impostate solo prima del caricamento della barra multifunzione.  Queste proprietà possono essere impostate in tre modi:  
  
-   Nella finestra **Proprietà** di Visual Studio.  
  
-   Nel costruttore della classe **Ribbon**.  
  
-   Nel metodo CreateRibbonExtensibilityObject della classe `ThisAddin`, `ThisWorkbook` o `ThisDocument` del progetto.  
  
 I menu dinamici presentano alcune eccezioni.  È possibile creare nuovi controlli, impostarne le proprietà e aggiungerli quindi a un menu dinamico in fase di esecuzione, anche dopo la barra multifunzione contenente il menu viene caricata.  
  
 Le proprietà dei controlli aggiunti a un menu dinamico possono essere impostate in qualsiasi momento.  
  
 Per ulteriori informazioni, vedere [Proprietà che diventano di sola lettura](#ReadOnlyProperties).  
  
### Impostazione di proprietà nel costruttore della barra multifunzione  
 È possibile impostare le proprietà di un controllo `Ribbon` nel costruttore della classe **Ribbon**.  È necessario che tale codice si trovi dopo la chiamata al metodo `InitializeComponent`.  Nell'esempio seguente viene aggiunto un nuovo pulsante a un gruppo se l'ora corrente corrisponde alle 17.00 ora del Pacifico \(UTC\-8\) o più tardi.  
  
 Aggiungere il codice riportato di seguito.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 In Visual c\# aggiornati da Visual Studio 2008, il costruttore viene visualizzato nel file di codice della barra multifunzione.  
  
 Nei progetti di Visual Basic., o Visual c\# creati in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], il costruttore viene visualizzato nel file di codice della finestra di progettazione della barra multifunzione.  Il file è *YourRibbonItem*. Designer.cs o *YourRibbonItem*. Designer.vb.  Nei progetti Visual Basic, per visualizzare il file è prima necessario fare clic sul pulsante **Mostra tutti i file** in Esplora soluzioni.  
  
### Impostazione di proprietà nel metodo CreateRibbonExtensibilityObject  
 È possibile impostare le proprietà di un controllo `Ribbon` quando si esegue l'override del metodo CreateRibbonExtensibilityObject in `ThisAddin`, `ThisWorkbook`, o nella classe `ThisDocument` del progetto.  Per ulteriori informazioni sul metodo CreateRibbonExtensibilityObject, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
 Le proprietà seguenti di esempio della barra multifunzione di set nel metodo CreateRibbonExtensibilityObject della classe `ThisWorkbook` di progetto cartella di lavoro di Excel.  
  
 Aggiungere il codice riportato di seguito.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> Proprietà che diventano di sola lettura  
 Nella tabella seguente vengono illustrate le proprietà che possono essere impostate solo prima del caricamento della barra multifunzione.  
  
> [!NOTE]  
>  È possibile impostare le proprietà dei controlli nei menu dinamici in qualsiasi momento.  In tal caso, questa tabella non è applicabile.  
  
|Proprietà|Classe del controllo della barra multifunzione|  
|---------------|----------------------------------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groups**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Nome**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tabs**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Titolo**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Impostazione di proprietà per barre multifunzione che sono visualizzate nei controlli Outlook  
 Una nuova istanza della barra multifunzione viene creata ogni volta che un utente apre un controllo in cui viene visualizzata la barra multifunzione.  Tuttavia, è possibile impostare le proprietà elencate nella tabella precedente solo prima della prima istanza della barra multifunzione.  Una volta creata la prima istanza, queste proprietà diventano di sola lettura perché la prima istanza definisce il file XML che Outlook utilizza per caricare la barra multifunzione.  
  
 Se si dispone di logica condizionale imposta una proprietà su un valore diverso quando altre istanze della barra multifunzione vengono create, tale codice non avrà effetto.  
  
> [!NOTE]  
>  Assicurarsi che la proprietà **Nome** viene impostata per ogni controllo che si aggiunge a una barra multifunzione di Outlook.  Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di esecuzione, è necessario impostare questa proprietà nel codice.  Se si aggiunge un controllo a una barra multifunzione di Outlook in fase di progettazione, la proprietà Name viene impostata automaticamente.  
  
## Eventi del controllo della barra multifunzione  
 Ogni classe di controllo contiene uno o più eventi.  Nella tabella riportata di seguito vengono descritti gli eventi.  
  
|Evento|Descrizione|  
|------------|-----------------|  
|Click|Si verifica quando si seleziona con il mouse un controllo.|  
|TextChanged|Si verifica quando il testo di una casella di modifica o di una casella combinata viene modificato.|  
|ItemsLoading|Si verifica quando la raccolta Items del controllo è richiesto da Office.  Office memorizza nella cache la raccolta Items fino a che il codice non modifica le proprietà del controllo o il metodo <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> non viene chiamato.|  
|ButtonClick|Si verifica quando si seleziona con il mouse un pulsante in un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> o <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>.|  
|SelectionChanged|Si verifica quando cambia la selezione in un controllo <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> o <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|  
|DialogLauncherClick|Si verifica quando si seleziona con il mouse l'icona dell'utilità di avvio della finestra di dialogo nell'angolo inferiore destro di un gruppo.|  
  
 I gestori di questi eventi hanno i seguenti due parametri.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*sender*|Un oggetto <xref:System.Object> che rappresenta il controllo che ha generato l'evento.|  
|*e*|Oggetto <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> che contiene <xref:Microsoft.Office.Core.IRibbonControl>.  Utilizzare questo controllo per accedere a qualsiasi proprietà non disponibile nel modello a oggetti della barra multifunzione fornito da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## Vedere anche  
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: aggiornamento dei controlli di una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personalizzazione di una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Procedura: personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)   
 [Procedura: aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  