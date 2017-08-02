---
title: "Controlli del contenuto"
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
  - "VST.Toolbox.DropDownListContentControl"
  - "VST.Toolbox.RichTextContentControl"
  - "VST.Toolbox.PlainTextContentControl"
  - "VST.Toolbox.ComboBoxContentControl"
  - "VST.Toolbox.CCBuildingBlockGalleryContentControl"
  - "VST.Toolbox.DatePickerContentControl"
  - "VST.Toolbox.PictureContentControl"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "compilazione della raccolta di blocchi [sviluppo per Office in Visual Studio]"
  - "BuildingBlockGalleryContentControl (classe)"
  - "ComboBoxContentControl (classe)"
  - "controlli del contenuto [sviluppo per Office in Visual Studio]"
  - "controlli del contenuto [sviluppo per Office in Visual Studio], informazioni sui controlli contenuto"
  - "controlli [sviluppo per Office in Visual Studio], controlli contenuto"
  - "parti XML personalizzate, controlli contenuto"
  - "associazione dati [sviluppo per Office in Visual Studio], controlli contenuto"
  - "DatePickerContentControl (classe)"
  - "blocchi di compilazione del documento [sviluppo per Office in Visual Studio]"
  - "documenti [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "DropDownListContentControl (classe)"
  - "GroupContentControl (classe)"
  - "documenti Office [sviluppo per Office in Visual Studio], autorizzazioni limitate"
  - "PictureContentControl (classe)"
  - "PlainTextContentControl (classe)"
  - "autorizzazioni limitate [sviluppo per Office in Visual Studio]"
  - "RichTextContentControl (classe)"
  - "modelli [sviluppo per Office in Visual Studio], controlli contenuto"
ms.assetid: ed59e522-dd6e-4c82-8d49-f5dbcfcc950d
caps.latest.revision: 65
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 64
---
# Controlli del contenuto
  I controlli contenuto permettono di progettare documenti e modelli che hanno le caratteristiche seguenti:  
  
-   Un'interfaccia utente che include input controllato, come un form.  
  
-   Restrizioni che impediscono agli utenti di modificare sezioni protette del documento o del modello.  Per altre informazioni, vedere [Protezione di parti di documenti mediante controlli contenuto](#Protection).  
  
-   Data binding a un'origine dati.  Per altre informazioni, vedere [Binding di dati a controlli contenuto](#DataBinding).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere [Binding di dati a controlli contenuto di Word 2007 con Visual Studio Tools per Office System  \(3.0\)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## Panoramica dei controlli contenuto  
 I controlli contenuto forniscono un'interfaccia utente ottimizzata sia per l'input utente sia per la stampa.  Quando si aggiunge un controllo contenuto a un documento, il controllo è identificato da un bordo, un titolo e testo temporaneo che può contenere istruzioni per l'utente.  Il bordo e il titolo del controllo non vengono visualizzati nelle versioni stampate del documento.  
  
 Ad esempio, se si vuole che l'utente immetta una data in una sezione del documento, è possibile aggiungere un controllo contenuto selezione data al documento.  Quando gli utenti fanno clic sul controllo, viene visualizzata l'interfaccia utente del controllo selezione data standard.  È anche possibile impostare le proprietà del controllo in modo da impostare il calendario locale visualizzato e specificare il formato di data.  Dopo che l'utente sceglie una data, l'interfaccia utente del controllo viene nascosta e la data viene visualizzata se l'utente stampa il documento.  
  
 I controlli contenuto semplificano anche le operazioni seguenti:  
  
-   Impedire agli utenti la modifica o l'eliminazione di parti di un documento.  Questa caratteristica è utile se un documento o un modello contiene informazioni che gli utenti devono poter leggere ma non modificare o se si vuole permettere agli utenti di modificare i controlli contenuto, ma non di eliminarli.  
  
-   Associare parti di un documento o di un modello a dati.  È possibile associare controlli contenuto a campi di database, oggetti gestiti in [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], elementi XML archiviati nel documento e altre origini dati.  
  
 Nei progetti a livello di documento è possibile aggiungere controlli contenuto al documento in fase di progettazione o di esecuzione.  Nei progetti di componente aggiuntivo VSTO è possibile aggiungere controlli contenuto a qualsiasi documento aperto in fase di esecuzione.  Per altre informazioni, vedere [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  È possibile usare controlli contenuto solo in documenti salvati in formato Open XML.  Non è possibile usare controlli contenuto in documenti salvati nel formato Documento di Word 97\-2003 \(\*.doc\).  
  
## Tipi di controlli contenuto  
 Sono disponibili nove diversi tipi di controlli contenuto che è possibile aggiungere ai documenti.  Per la maggior parte dei controlli contenuto è presente un tipo corrispondente nello spazio dei nomi <xref:Microsoft.Office.Tools.Word>.  È anche possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> generico, che può rappresentare uno qualsiasi dei controlli contenuto disponibili.  Per una procedura dettagliata che mostra come usare ognuno dei controlli contenuto disponibili, vedere [Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### Raccolta di blocchi predefiniti  
 Una raccolta di blocchi predefiniti permette agli utenti di selezionare una voce da un elenco di *blocchi predefiniti del documento* da inserire in un documento.  Un blocco predefinito del documento è una parte di contenuto creata per essere usata più volte, come un frontespizio comune, una tabella formattata o un'intestazione.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>.  Per altre informazioni sui blocchi predefiniti, vedere [Novità per gli sviluppatori in Word 2007](http://msdn.microsoft.com/it-it/74aa6688-65b3-4167-997d-131f26ad8f84).  
  
### Casella di controllo  
 Una casella di controllo fornisce un'interfaccia utente che rappresenta uno stato binario: selezionato o deselezionato.  
  
 Diversamente da altri tipi di controlli contenuto, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non include un tipo specifico che rappresenta un controllo contenuto casella di controllo.  In altre parole, non esiste alcun tipo CheckBoxContentControl.  Tuttavia, è comunque possibile creare un controllo contenuto casella di controllo aggiungendo un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> generico a un documento a livello di codice.  Per altre informazioni, vedere [Controlli contenuto casella di controllo in progetti di Word](#checkbox).  
  
### Casella combinata  
 Una casella combinata visualizza un elenco di voci che possono essere selezionate dall'utente.  Diversamente da un elenco a discesa, la casella combinata permette agli utenti di aggiungere voci proprie.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
### Selezione data  
 Un controllo selezione data fornisce un'interfaccia utente calendario per la selezione di una data.  Il calendario viene visualizzato quando l'utente finale fa clic sulla freccia a discesa nel controllo.  È possibile usare calendari locali e formati di data diversi.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
### Elenco a discesa  
 Un elenco a discesa visualizza un elenco di voci che possono essere selezionate dagli utenti.  Diversamente da una casella combinata, l'elenco a discesa non permette agli utenti di aggiungere o modificare voci.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>.  
  
### Gruppo  
 Un controllo gruppo definisce un'area protetta di un documento che non può essere modificata o eliminata dagli utenti.  Un controllo gruppo può contenere qualsiasi elemento del documento, come testo, tabelle, grafica e altri controlli contenuto.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
### Immagine  
 Un controllo immagine visualizza un'immagine.  È possibile specificare l'immagine in fase di progettazione o in fase di esecuzione oppure gli utenti possono fare clic su questo controllo per selezionare un'immagine da inserire nel documento.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.PictureContentControl>.  
  
### Formato RTF  
 Un controllo in formato RTF contiene testo o altri elementi, come tabelle, immagini o altri controlli contenuto.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.  
  
### Testo normale  
 Un controllo testo normale contiene testo.  Un controllo testo normale non può contenere altri elementi, come tabelle, immagini o altri controlli contenuto.  Inoltre, tutto il testo presente in un controllo testo normale ha la stessa formattazione.  Ad esempio, se si applica il corsivo a una parola di una frase contenuta in un controllo testo normale, tutto il testo all'interno del controllo sarà in corsivo.  Per altre informazioni, vedere il tipo <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>.  
  
### Controllo contenuto generico  
 Un controllo contenuto generico è un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> che può rappresentare uno qualsiasi dei tipi di controllo contenuto disponibili.  È possibile modificare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> perché si comporti come un tipo diverso di controllo contenuto usando la proprietà <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A>.  Ad esempio, se si crea un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> che rappresenta un controllo testo normale, è possibile modificarlo in fase di esecuzione perché si comporti come una casella combinata.  
  
 È possibile creare oggetti <xref:Microsoft.Office.Tools.Word.ContentControl> solo in fase di esecuzione e non in fase di progettazione.  Per altre informazioni, vedere [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## Funzionalità comuni dei controlli contenuto  
 La maggior parte dei controlli contenuto condivide un set di membri che è possibile usare per eseguire attività comuni.  La tabella seguente descrive alcune delle attività che è possibile eseguire usando questi membri.  
  
|Per questa attività:|Eseguire questa operazione:|  
|--------------------------|---------------------------------|  
|Ottenere o impostare il testo visualizzato nel controllo.|Usare la proprietà **Text**. **Note:**  Questa proprietà non è disponibile per i tipi <xref:Microsoft.Office.Tools.Word.PictureContentControl> e <xref:Microsoft.Office.Tools.Word.ContentControl>.|  
|Ottenere o impostare il testo temporaneo visualizzato nel controllo fino a quando un utente non modifica il controllo, nel controllo non vengono immessi dati di un'origine dati o il contenuto del controllo non viene eliminato.|Usare la proprietà **PlaceholderText**. **Note:**  Questa proprietà non è disponibile per il tipo <xref:Microsoft.Office.Tools.Word.PictureContentControl>.|  
|Ottenere o impostare il titolo visualizzato nel bordo del controllo contenuto quando l'utente fa clic sul bordo.|Usare la proprietà **Title**.|  
|Rimuovere automaticamente il controllo dal documento dopo che l'utente modifica il controllo.  Il testo all'interno del controllo resta nel documento.|Usare la proprietà **Temporary**.|  
|Eseguire codice quando l'utente fa clic nel controllo contenuto o quando il cursore viene spostato a livello di codice nel controllo contenuto.|Gestire l'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> del controllo.|  
|Eseguire codice quando l'utente fa clic all'esterno del controllo contenuto o quando il cursore viene spostato all'esterno del controllo contenuto a livello di codice.|Gestire l'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> del controllo.|  
|Eseguire codice dopo l'aggiunta del controllo contenuto al documento come risultato di un'operazione di annullamento o ripetizione.|Gestire l'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> del controllo.|  
|Eseguire codice appena prima che il controllo contenuto venga eliminato dal documento.|Gestire l'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> del controllo.|  
  
##  <a name="Protection"></a> Protezione di parti di documenti mediante controlli contenuto  
 Quando si protegge una parte di un documento, si impedisce agli utenti di modificare o eliminare il contenuto di tale parte.  È possibile proteggere parti di un documento mediante controlli contenuto in diversi modi.  
  
 Se l'area che si vuole proteggere si trova all'interno di un controllo contenuto, è possibile usare le proprietà del controllo contenuto per impedire agli utenti di modificare o eliminare il controllo:  
  
-   La proprietà **LockContents** impedisce agli utenti di modificare il contenuto.  
  
-   La proprietà **LockContentControl** impedisce agli utenti di eliminare il controllo.  
  
 Se l'area che si vuole proteggere non si trova all'interno di un controllo contenuto o se si vuole proteggere un'area che include controlli contenuto e altri tipi di contenuto, è possibile inserire l'intera area in un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Diversamente da altri controlli contenuto, un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> non fornisce alcuna interfaccia utente visibile all'utente.  Il suo unico scopo è definire un'area che non può essere modificata dagli utenti.  
  
> [!NOTE]  
>  Se si crea un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> che include controlli contenuto incorporati, questi non vengono automaticamente protetti.  È necessario usare la proprietà **LockContents** di ogni controllo incorporato per impedire agli utenti di modificarne il contenuto.  
  
 Per altre informazioni su come usare controlli contenuto per proteggere parti di documenti, vedere [Procedura: proteggere parti di documenti mediante i controlli del contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a> Binding di dati a controlli contenuto  
 È possibile visualizzare dati nei documenti mediante il binding di un controllo contenuto a un'origine dati.  Quando l'origine dati viene aggiornata, il controllo contenuto riflette le modifiche.  È anche possibile salvare le modifiche di nuovo nell'origine dati.  
  
 I controlli contenuto offrono le opzioni di data binding seguenti:  
  
-   È possibile associare controlli contenuto a campi di database o oggetti gestiti usando lo stesso modello di data binding di Windows Form.  
  
-   È possibile associare controlli contenuto a elementi in parti del codice XML \(chiamate anche *parti XML personalizzate*\) incorporate nel documento.  
  
 Per una panoramica del binding di controlli host in soluzioni di Office a dati, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### Uso del modello di data binding di Windows Form  
 La maggior parte dei controlli contenuto supporta il modello di data binding semplice usato da Windows Form.  Il data binding semplice significa che un controllo è associato a un singolo elemento dati, ad esempio un valore in una colonna di una tabella dati.  Per altre informazioni, vedere [Associazione dati e Windows Form](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
 Nei progetti a livello di documento è possibile associare dati a controlli contenuto usando la finestra **Origini dati** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per altre informazioni su come aggiungere ai documenti controlli contenuto associati a dati, vedere [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md) e [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 La tabella seguente elenca i controlli contenuto che è possibile associare a ogni tipo di dati nella finestra **Origini dati**.  
  
|Tipo di dati|Controllo contenuto predefinito|Altri controlli contenuto che è possibile associare a questo tipo di dati|  
|------------------|-------------------------------------|-------------------------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> Matrice <xref:System.Byte>|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Nessuna|  
  
 Nei progetti a livello di documento e di componente aggiuntivo VSTO è possibile associare a livello di codice un controllo contenuto a un'origine dati usando il metodo <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> della proprietà <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> del controllo.  In questo caso, passare la stringa **Text** al parametro *propertyName* del metodo <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A>.  La proprietà **Text** è la proprietà di data binding predefinita dei controlli contenuto.  
  
 I controlli contenuto supportano anche il data binding bidirezionale, in cui le modifiche nel controllo vengono aggiornate nell'origine dati.  Per altre informazioni, vedere [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  I controlli contenuto non supportano il data binding complesso.  Se si associa un oggetto <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> a un'origine dati usando il modello di dati di Windows Form, gli utenti visualizzeranno un solo valore quando fanno clic sul controllo.  Per associare questi controlli a un set di valori di dati da cui gli utenti possono scegliere, è possibile associare i controlli a elementi in una parte XML personalizzata.  
  
### Binding di controlli contenuto a parti XML personalizzate  
 È possibile associare alcuni controlli contenuto a elementi in parti XML personalizzate incorporate nel documento.  Per altre informazioni sulle parti XML personalizzate, vedere [Cenni preliminari sulle web part XML personalizzate](../vsto/custom-xml-parts-overview.md).  
  
 Per associare un controllo contenuto a un elemento in una parte XML personalizzata, usare la proprietà **XMLMapping** del controllo.  L'esempio di codice seguente mostra come associare un oggetto <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> all'elemento `Price` all'interno del nodo `Product` in una parte XML personalizzata che è già stata aggiunta al documento.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 Per una procedura che mostra in modo più dettagliato come associare controlli contenuto a parti XML personalizzate, vedere [Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Quando si associa un controllo contenuto a una parte XML personalizzata, viene automaticamente attivato il data binding bidirezionale.  Se un utente modifica testo nel controllo, gli elementi XML corrispondenti vengono automaticamente aggiornati.  Analogamente, se si modificano i valori degli elementi nelle parti XML personalizzate, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati.  
  
 È possibile associare i tipi seguenti di controlli contenuto a parti XML personalizzate:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### Eventi di data binding per controlli contenuto  
 Tutti i controlli contenuto forniscono un set di eventi che è possibile gestire per eseguire attività correlate ai dati, come la convalida per determinare che il testo in un controllo soddisfi determinati criteri prima dell'aggiornamento dell'origine dati.  La tabella seguente elenca gli eventi controllo contenuto correlati al data binding.  
  
|Attività|Evento|  
|--------------|------------|  
|Eseguire codice appena prima che Word aggiorni automaticamente il testo in un controllo contenuto associato a una parte XML personalizzata.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Eseguire codice appena prima che Word aggiorni automaticamente i dati in una parte XML personalizzata associata a un controllo contenuto \(ovvero dopo che il testo presente nel controllo contenuto cambia\).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Eseguire codice personalizzato per convalidare il contenuto del controllo in base a criteri personalizzati.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Eseguire codice dopo la convalida corretta del contenuto del controllo.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## Limitazioni dei controlli contenuto  
 Quando si usano controlli contenuto nei progetti di Office, tenere presenti le limitazioni seguenti.  
  
### Differenze di comportamento tra la fase di progettazione e quella di esecuzione  
 Molte delle limitazioni imposte da Microsoft Office Word ai controlli contenuto in fase di esecuzione non si applicano alla fase di progettazione.  Quando si progetta l'interfaccia utente di una soluzione a livello di documento in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], assicurarsi di modificare i controlli contenuto solo in modi supportati in fase di esecuzione.  
  
 Se si modifica un controllo contenuto in fase di progettazione in un modo non supportato dal controllo in fase di esecuzione, la finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non segnala le modifiche non supportate.  Tuttavia, quando il progetto viene sottoposto a debug o eseguito oppure viene salvato e riaperto, Word visualizza un messaggio di errore e richiede l'autorizzazione per ripristinare il documento.  Quando si ripristina il documento, Word rimuove tutta la formattazione e tutto il contenuto non supportati dal controllo.  
  
 Ad esempio, Word non impedisce di aggiungere una tabella a un oggetto <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> in fase di progettazione.  Tuttavia, poiché gli oggetti <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> non possono contenere tabelle in fase di esecuzione, Word visualizzerà un messaggio di errore all'apertura del documento.  
  
 Inoltre, molte delle proprietà che definiscono il comportamento dei controlli contenuto non hanno effetto in fase di progettazione.  Ad esempio, se si imposta la proprietà **LockContents** di un controllo contenuto su **True** in fase di progettazione, è comunque possibile modificare il testo nel controllo nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Questa proprietà impedisce all'utente solo di modificare il controllo in fase di esecuzione.  
  
### Limitazioni degli eventi  
 I controlli contenuto non forniscono la generazione di un evento quando l'utente modifica il testo o altri elementi nel controllo.  Ad esempio, non viene generato alcun evento quando un utente seleziona un elemento diverso in un oggetto <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> o <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Per determinare i momenti in cui un utente modifica il contenuto di un controllo contenuto, è possibile associare il controllo a una parte XML personalizzata e quindi gestire l'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>.  Questo evento viene generato quando l'utente modifica il contenuto di un controllo associato a una parte XML personalizzata.  Per una procedura dettagliata su come associare un controllo contenuto a una parte XML personalizzata, vedere [Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a> Controlli contenuto casella di controllo in progetti di Word  
 In Word 2010 è stato introdotto un nuovo tipo di controllo contenuto, che rappresenta una casella di controllo.  Tuttavia, il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non fornisce un tipo CheckBoxContentControl corrispondente da usare in progetti di Office.  Per creare un controllo contenuto casella di controllo in un progetto di [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o Word 2010, usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> per creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> e passare il valore <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> al metodo per specificare un controllo contenuto casella di testo.  Nell'esempio di codice seguente viene illustrato come procedere.  
  
 [!code-csharp[Trin_ContentControlReference#800](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/checkbox.cs#800)]
 [!code-vb[Trin_ContentControlReference#800](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/checkbox.vb#800)]  
  
## Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  