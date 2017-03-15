---
title: "Utilizzo di elementi in XAML Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilizzo di elementi in XAML Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile aggiungere elementi, come controlli, layout e forme, all'app in XAML, nel codice o usando la finestra di progettazione XAML.  Questo argomento descrive come usare gli elementi nella finestra di progettazione XAML in Visual Studio o in Blend per Visual Studio.  
  
## Aggiunta di un elemento a un layout  
 Per *layout* si intende il processo di ridimensionamento e posizionamento degli elementi in un'interfaccia utente.  Per posizionare elementi visivi, è necessario includerli in un oggetto [Panel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx) di layout.  Un oggetto `Panel` include una proprietà figlio che è una raccolta di tipi [FrameworkElement](http://msdn.microsoft.com/library/windows/apps/br208706.aspx).  È possibile usare diversi elementi figlio di `Panel`, come [Canvas](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx) e [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx), perché fungano da contenitori di layout e per posizionare e disporre gli elementi su una pagina.  
  
 Per impostazione predefinita, viene usato un pannello `Grid` come contenitore di layout di primo livello all'interno di una pagina o di un modulo.  È possibile aggiungere pannelli, controlli o altri elementi di layout all'interno del layout di pagina di primo livello.  
  
#### Per aggiungere un elemento a un layout  
  
-   Nella finestra di progettazione XAML eseguire una delle operazioni seguenti:  
  
    -   Fare doppio clic su un elemento nella **Casella degli strumenti** oppure selezionare un elemento nella Casella degli strumenti e premere INVIO.  
  
    -   Trascinare un elemento dalla **Casella degli strumenti** alla tavola da disegno.  
  
    -   Nella **Casella degli strumenti** selezionare uno degli strumenti di disegno, ad esempio [Ellipse](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) o [Rectangle](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx), e quindi disegnare un elemento nel pannello attivo.  
  
## Modifica dell'ordine dei livelli degli elementi  
 Quando sono presenti due elementi nella tavola da disegno nella finestra di progettazione XAML, uno appare davanti all'altro nell'ordine dei livelli.  Alla fine dell'elenco di elementi nella finestra Struttura documento si trova l'elemento in primo piano, eccetto quando è impostata una proprietà **ZIndex** per un elemento.  Quando si inserisce un elemento in una pagina, un modulo o un contenitore di layout, l'elemento viene automaticamente posizionato davanti agli altri nell'elemento contenitore attivo.  Per modificare l'ordine degli elementi, è possibile usare i comandi **Ordine** o trascinare gli elementi nell'albero di oggetti nella finestra Struttura documento.  
  
#### Per modificare l'ordine dei livelli  
  
-   Eseguire una delle operazioni seguenti:  
  
    -   Nella finestra **Struttura documento** trascinare gli elementi verso l'alto o verso il basso per creare l'ordine dei livelli desiderato.  
  
    -   Fare clic con il pulsante destro del mouse nella finestra Struttura documento o nella tavola da disegno per cui si vuole modificare l'ordine dei livelli e scegliere **Ordine**, quindi fare clic su una delle opzioni seguenti:  
  
        -   **Porta in primo piano** per portare l'elemento davanti a tutti gli altri nell'ordine.  
  
        -   **Porta avanti** per portare l'elemento avanti di un livello nell'ordine.  
  
        -   **Porta indietro** per portare l'elemento indietro di un livello nell'ordine.  
  
        -   **Porta in secondo piano** per portare l'elemento dietro a tutti gli altri nell'ordine.  
  
     Modificare la proprietà **ZIndex** nella sezione **Layout** della finestra Proprietà.  Per gli elementi che si sovrappongono, la proprietà **ZIndex** ha la precedenza sull'ordine degli elementi indicato nella finestra Struttura documento.  Un elemento con un valore **ZIndex** inferiore viene visualizzato in primo piano quando gli elementi si sovrappongono.  
  
## Modifica dell'allineamento di un elemento  
 È possibile allineare elementi nella tavola da disegno usando i comandi di menu o trascinando gli elementi sulle guide di allineamento.  
  
 Una *guida di allineamento* è un indizio visivo che aiuta ad allineare un elemento rispetto agli altri nell'app.  
  
#### Per allineare due o più elementi tramite i comandi di menu  
  
1.  Selezionare gli elementi da allineare.  È possibile selezionare uno o più elementi tenendo premuto CTRL mentre li si selezionano.  
  
2.  Selezionare una delle proprietà seguenti in **HorizontalAlignment** nella sezione **Layout** della finestra Proprietà: **A sinistra**, **Al centro**, **A destra** o **Stretch**.  
  
3.  Selezionare una delle proprietà seguenti in **VerticalAlignment** nella sezione **Layout** della finestra Proprietà: **In alto**, **Al centro**, **In basso** o **Stretch**.  
  
#### Per allineare due o più elementi tramite le guide di allineamento  
  
-   In un layout che contiene almeno due elementi nella finestra di progettazione XAML trascinare o ridimensionare uno degli elementi in modo che il bordo sia allineato a un altro elemento.  
  
     Quando i bordi sono allineati, viene visualizzato un *limite di allineamento* per indicare l'allineamento.  Il limite di allineamento è indicato attraverso una riga tratteggiata rossa.  I limiti di allineamento vengono visualizzati solo quando è abilitato l'**allineamento alle guide di allineamento**.  Per un'illustrazione della tavola da disegno con un limite di allineamento, vedere [Creazione di un'interfaccia utente tramite XAML Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
## Modifica dei margini di un elemento  
 I margini nella finestra di progettazione XAML determinano la quantità di spazio vuoto attorno a un elemento sulla tavola da disegno.  Ad esempio, i margini specificano la quantità di spazio tra i bordi esterni di un elemento e i limiti di un pannello `Grid` che contiene l'elemento.  I margini specificano anche la quantità di spazio tra gli elementi contenuti in un oggetto `StackPanel`.  
  
#### Per modificare i margini di un elemento nella finestra Proprietà  
  
1.  Selezionare l'elemento di cui si vuole modificare i margini.  
  
2.  In **Layout** nella finestra Proprietà modificare il valore \(in pixel o unità indipendenti, che corrispondono all'incirca a 0,26 mm\) per qualsiasi proprietà **Margine** \(**Superiore**, **Sinistro**, **Destro** o **Inferiore**\).  
  
#### Per modificare i margini di un elemento nella tavola da disegno  
  
-   Per modificare i margini di un elemento rispetto al suo contenitore di layout, fare clic sugli *Adorner dei margini* visualizzati attorno all'elemento nella tavola da disegno quando l'elemento è selezionato e si trova all'interno di un contenitore di layout.  Per un'illustrazione degli Adorner dei margini, vedere [Creazione di un'interfaccia utente tramite XAML Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).  
  
     Se l'Adorner di un margine è aperto, in verticale o in orizzontale, il margine non è impostato.  Se l'Adorner di un margine è chiuso, il margine è impostato.  
  
     Quando si apre l'Adorner di un margine e il margine opposto non è impostato, questo viene impostato sul valore corretto in base alla posizione dell'elemento nella tavola da disegno.  Per i margini opposti, come i margini **Sinistro** e **Destro**, è sempre impostata almeno una proprietà.  
  
    > [!IMPORTANT]
    >  Gli elementi posizionati all'interno di alcuni contenitori di layout, come <xref:Windows.UI.Xaml.Controls.Canvas>, non hanno Adorner dei margini.  Gli elementi posizionati all'interno di un oggetto <xref:Windows.UI.Xaml.Controls.StackPanel> hanno Adorner dei margini per i margini sinistro e destro o superiore e inferiore, a seconda dell'orientamento di `StackPanel`.  
  
## Raggruppamento e separazione di elementi  
 Il raggruppamento di due o più elementi nella finestra di progettazione XAML comporta la creazione di un nuovo contenitore di layout e l'inserimento di questi elementi nel contenitore.  L'inserimento di due o più elementi insieme in un contenitore di layout permette di selezionare, spostare e trasformare facilmente il gruppo come se gli elementi del gruppo fossero un unico elemento.  Il raggruppamento è anche utile per identificare gli elementi correlati gli uni agli altri in qualche modo, ad esempio i pulsanti che costituiscono un elemento di navigazione.  Quando si separano elementi, si elimina semplicemente il contenitore di layout che li contiene.  
  
#### Per raggruppare elementi in un nuovo contenitore di layout  
  
1.  Selezionare gli elementi da raggruppare.  Per selezionare più elementi, fare clic su ognuno tenendo premuto CTRL.  
  
2.  Fare clic con il pulsante destro del mouse sugli elementi selezionati, scegliere **Raggruppa** e quindi fare clic sul tipo di contenitore di layout in cui si vuole inserire il gruppo.  
  
    > [!TIP]
    >  Se si seleziona <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer> per raggruppare gli elementi, questi vengono inseriti in un nuovo pannello <xref:Windows.UI.Xaml.Controls.Grid> all'interno di <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>.  Se si separano elementi in uno di questi contenitori di layout, viene eliminato solo <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> o <xref:Windows.UI.Xaml.Controls.ScrollViewer>, mentre il pannello <xref:Windows.UI.Xaml.Controls.Grid> viene mantenuto.  Per eliminare il pannello `Grid`, separare gli elementi di nuovo.  
  
#### Per separare elementi ed eliminare il layout  
  
-   Fare clic con il pulsante destro del mouse sul gruppo che si vuole separare e scegliere **Separa**.  
  
 È anche possibile raggruppare o separare elementi facendo clic con il pulsante destro del mouse sugli elementi selezionati nella finestra Struttura documento e scegliendo **Raggruppa** o **Separa**.  
  
## Reimpostazione del layout degli elementi  
 È possibile ripristinare i valori predefiniti per le proprietà di layout specifiche di un elemento usando i comandi di reimpostazione del layout.  Usando questi comandi, è possibile reimpostare margini, allineamento, larghezza, altezza e dimensioni di un elemento, singolarmente o collettivamente.  
  
#### Per reimpostare il layout degli elementi  
  
-   Nella finestra Struttura documento o nella tavola da disegno fare clic con il pulsante destro del mouse sull'elemento, scegliere **Layout** e **Reimposta** *NomeProprietà*, dove *NomeProprietà* è la proprietà che si vuole reimpostare \(oppure scegliere **Layout**, **Reimposta tutto** per reimpostare tutte le proprietà di layout per l'elemento\).  
  
## Vedere anche  
 [Creazione di un'interfaccia utente tramite XAML Designer](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)