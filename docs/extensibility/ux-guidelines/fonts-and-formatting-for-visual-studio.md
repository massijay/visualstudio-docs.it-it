---
title: "I tipi di carattere e la formattazione per Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c3df69-83b4-4fd0-b5b1-e18c33f39376
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# I tipi di carattere e la formattazione per Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_TheEnvironmentFont"></a> Il tipo di carattere ambiente  
 Tutti i caratteri all'interno di Visual Studio devono essere esposto all'utente per la personalizzazione. Ciò avviene principalmente attraverso il **tipi di carattere e colori** nella pagina di **Strumenti \> Opzioni** finestra di dialogo. Le tre categorie principali di impostazioni dei caratteri sono:  
  
-   **Tipo di carattere ambiente** ovvero il tipo di carattere primario per l'IDE \(ambiente di sviluppo integrato\), utilizzato per tutti gli elementi di interfaccia, incluse le finestre di dialogo, menu, finestre e finestre di documento. Per impostazione predefinita, il tipo di carattere ambiente è associato a un tipo di carattere di sistema che viene visualizzato come 9 punti Segoe UI nelle versioni correnti di Windows. Utilizzo di un tipo di carattere per tutti gli elementi dell'interfaccia consente di garantire un aspetto coerente del carattere nell'IDE.  
  
-   **Editor di testo** gli elementi che area nel codice e altri editor basati su testo può essere personalizzato nell'Editor di testo nella pagina **Strumenti \> Opzioni**.  
  
-   **Raccolte specifiche** finestre di progettazione che offrono personalizzazione dell'utente dei relativi elementi di interfaccia può esporre tipi di carattere specifico alla progettazione della superficie di attacco nella propria pagina Impostazioni **Strumenti \> Opzioni**.  
  
### Personalizzazione editor di tipi di carattere e il ridimensionamento  
 Gli utenti spesso saranno ingrandire o ingrandire le dimensioni e\/o il colore del testo nell'editor in base alle loro preferenze, indipendente dell'interfaccia utente generali. Poiché il tipo di carattere ambiente viene utilizzato su elementi che potrebbero essere visualizzate all'interno o come parte di un editor o la finestra di progettazione, è importante notare il comportamento previsto quando viene modificata una delle classificazioni seguenti tipi di carattere.  
  
 Durante la creazione di elementi dell'interfaccia utente che vengono visualizzati nell'editor, ma sono non fa parte di *contenuto*, è importante utilizzare il tipo di carattere ambiente e non il testo in modo da elementi ridimensionati in modo prevedibile.  
  
1.  Per il testo nell'editor di codice, ridimensionare con l'impostazione del carattere testo codice e rispondere a livello di zoom del testo dell'editor.  
  
2.  Tutti gli altri elementi dell'interfaccia devono essere collegati al tipo di carattere ambiente e rispondono alle modifiche globale nell'ambiente. Questo include \(ma non è limitato a\):  
  
    -   Testo nel menu di scelta rapida  
  
    -   Testo in un'area di controllo di editor, ad esempio testo del menu lampadina, veloce trovare riquadro dell'editor e passare al riquadro  
  
    -   Testo dell'etichetta nelle finestre di dialogo, ad esempio la ricerca nei file o eseguire il refactoring  
  
### L'accesso il tipo di carattere ambiente  
 Nel codice nativo o Windows Form, il tipo di carattere ambiente sono accessibili tramite il metodo **IUIHostLocale::GetDialogFont** dopo l'esecuzione di query l'interfaccia del servizio SID\_SUIHostLocale.  
  
 Per Windows Presentation Foundation \(WPF\), derivare la classe della finestra di dialogo della shell **DialogWindow** classe invece di WPF **finestra** \(classe\).  
  
 Nel codice XAML, il codice simile al seguente:  
  
```  
<ui:DialogWindow x:Class"MyNameSpace.MyWindow" xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:s="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:ui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0" ShowInTaskbar="False" WindowStartupLocation="CenterOwner" Title="My Dialog"> </ui:DialogWindow> code behind: internal partial class WebConfigModificationWindow : DialogWindow { }  
  
```  
  
 \(Sostituire `Microsoft.VisualStudio.Shell.11.0` con la versione corrente della dll MPF.\)  
  
 Per visualizzare la finestra di dialogo, chiamare "**ShowModal \(\)**" nella classe su **OpenFileDialog**.**ShowModal \(\)** imposta lo stato modale corretto nella shell, assicura la finestra di dialogo è centrato nella finestra padre e così via.  
  
 Il codice è indicato di seguito:  
  
```  
MyWindow window = new MyWindow(); window.ShowModal()  
  
```  
  
 **ShowModal** restituisce un valore booleano? \(valore booleano che ammette valori null\) con il **DialogResult**, che può essere utilizzato se necessario. Il valore restituito è true se è stata chiusa la finestra di dialogo con **OK**.  
  
 Se si desidera visualizzare alcune UI WPF che non è una finestra di dialogo e ospitata nella propria **HwndSource**, ad esempio una finestra popup o una finestra figlio WPF di una finestra padre di Win32\/Windows Form, sarà necessario impostare il **FontFamily** e **FontSize** per l'elemento radice dell'elemento WPF. \(La shell imposta le proprietà nella finestra principale, ma non viene ereditate oltre un HWND\). La shell fornisce risorse a cui possono essere associate le proprietà e simile al seguente:  
  
```  
<Setter property="FontFamily" Value="{DynamicResource VsFont.EnvironmentFontFamily}" /> <Setter property="FontSize" Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
  
```  
  
###  <a name="BKMK_Formatting"></a> Formattazione di riferimento \(scalabilità\/formattazione in grassetto\)  
 Alcune finestre di dialogo richiedono particolare testo in grassetto o una dimensione diversa da quella di tipo di carattere ambiente. Tipi di carattere maggiori di tipo di carattere ambiente erano in precedenza, codificato come "tipo di carattere ambiente \+ 2" o simili. Utilizzando i frammenti di codice forniti verranno supporta monitor ad alta risoluzione e verificare che per visualizzare il testo viene visualizzato sempre le dimensioni corrette e peso \(ad esempio Light o Semilight\).  
  
> **Nota: Prima di applicare la formattazione, assicurarsi si seguono le linee guida fornite in [Stile del testo](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).**  
  
 Per ridimensionare il tipo di carattere ambiente, impostare lo stile del controllo TextBlock o etichetta come indicato. Ognuno di questi frammenti di codice, viene utilizzati correttamente, verrà generato il tipo di carattere corretto, tra cui le variazioni di dimensioni e peso appropriate.  
  
 Dove "vsui" è un riferimento allo spazio dei nomi Microsoft.VisualStudio.Shell:  
  
```  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
```  
  
#### Tipo di carattere ambiente 375% \+ Light  
 **Viene visualizzato come:** pt 34 Segoe UI Light  
  
 **Utilizzare per:** \(rari\) univoco personalizzata dell'interfaccia utente, come ad esempio la pagina iniziale  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment375PercentFontSizeStyleKey}}">TextBlock: 375 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment375PercentFontSizeStyleKey}}">Label: 375 Percent Scaling</Label>  
  
```  
  
#### Tipo di carattere ambiente 310% \+ Light  
 **Viene visualizzato come:** pt 28 Segoe UI Light  
  
 **Utilizzare per:** titoli finestra di dialogo firma di grandi dimensioni, la voce report principali  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment310PercentFontSizeStyleKey}}">TextBlock: 310 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment310PercentFontSizeStyleKey}}">Label: 310 Percent Scaling</Label>  
  
```  
  
#### Tipo di carattere ambiente 200% \+ Semilight  
 **Viene visualizzato come:** 18 pt Segoe UI Semilight  
  
 **Utilizzare per:** sottotitoli, i titoli di finestre di dialogo di piccole e medie dimensioni  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment200PercentFontSizeStyleKey}}">TextBlock: 200 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment200PercentFontSizeStyleKey}}">Label: 200 Percent Scaling</Label>  
  
```  
  
#### Tipo di carattere ambiente 155%  
 **Viene visualizzato come:** 14 pt Segoe UI  
  
 **Utilizzare per:** intestazioni di sezione nel documento e dell'interfaccia utente o i report  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment155PercentFontSizeStyleKey}}">TextBlock: 155 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment155PercentFontSizeStyleKey}}">Label: 155 Percent Scaling</Label>  
  
```  
  
#### Tipo di carattere ambiente 133%  
 **Viene visualizzato come:** 12 pt Segoe UI  
  
 **Utilizzare per:** sottotitoli più piccoli in finestre di dialogo di firma e di documento e dell'interfaccia utente  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment133PercentFontSizeStyleKey}}">TextBlock: 133 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment133PercentFontSizeStyleKey}}">Label: 133 Percent Scaling</Label>  
  
```  
  
#### Tipo di carattere ambiente 122%  
 **Viene visualizzato come:** 11 pt Segoe UI  
  
 **Utilizzare per:** sezione intestazioni nelle finestre di dialogo firma, dall'alto nodi nella visualizzazione ad albero, spostamento di tabulazione verticale  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironment122PercentFontSizeStyleKey}}">TextBlock: 122 Percent Scaling</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironment122PercentFontSizeStyleKey}}">Label: 122 Percent Scaling</Label>  
  
```  
  
#### Tipo di carattere ambiente \+ grassetto  
 **Viene visualizzato come:** in grassetto 9 punti Segoe UI  
  
 **Utilizzare per:** etichette e i sottotitoli in finestre di dialogo firma, report e documenti e dell'interfaccia utente  
  
 **Codice procedurale:** dove "textBlock" è un elemento TextBlock precedentemente definito e "label" è un'etichetta definita in precedenza.  
  
```  
textBlock.SetResourceReference(TextBlock.StyleProperty, VsResourceKeys.TextBlockEnvironmentBoldStyleKey); label.SetResourceReference(Label.StyleProperty, VsResourceKeys.LabelEnvironmentBoldStyleKey);  
  
```  
  
 **XAML:** impostare lo stile del controllo TextBlock o etichetta, come illustrato.  
  
```  
<TextBlock Style="{DynamicResource {x:Static vsui:VsResourceKeys.TextBlockEnvironmentBoldStyleKey}}"> Bold TextBlock</TextBlock> <Label Style="{DynamicResource {x:Static vsui:VsResourceKeys.LabelEnvironmentBoldStyleKey}}"> Bold Label</Label>  
  
```  
  
### Stili localizzabili  
 In alcuni casi, i localizzatori dovranno modificare gli stili dei caratteri per impostazioni locali diverse, ad esempio la rimozione di formattazione in grassetto dal testo per lingue asiatiche orientali. Per rendere possibile la localizzazione degli stili di carattere, gli stili devono essere all'interno del file. resx. Il modo migliore per farlo e modificare gli stili dei caratteri in Progettazione form di Visual Studio è impostata in modo esplicito gli stili del carattere in fase di progettazione. Anche se si crea un oggetto font completo e potrebbe sembrare l'ereditarietà dei tipi di carattere padre, solo la proprietà FontStyle viene utilizzata per impostare il tipo di carattere.  
  
 La soluzione consiste nel collegare il modulo di finestra di dialogo **FontChanged** evento. Nel **FontChanged** evento, esaminare tutti i controlli e verificare se il carattere è impostato. Se è impostato, modificarlo in un nuovo tipo di carattere in base alle carattere del form e lo stile del controllo precedente. È un esempio di codice:  
  
```  
private void Form1_FontChanged(object sender, System.EventArgs e) { SetFontStyles(); } /// <summary> /// SetFontStyles - This function will iterate all controls on a page /// and recreate their font with the desired fontstyle. /// It should be called in the OnFontChanged handler (and also in the constructor /// in case the IUIService is not available so OnFontChange doesn't fire). /// This way, when the VS shell font is given to us the controls that have /// a different style for the font (bolded for example) will recreate their font /// and use the VS shell font but with a style variation (bolded ...). /// </summary> protected void SetFontStyles() { SetFontStyles(this, this, this.Font); } protected static void SetFontStyles(Control topControl, Control parent, Font referenceFont) { foreach(Control c in parent.Controls) { if (c.Controls != null && c.Controls.Count > 0) { SetFontStyles(topControl, c, referenceFont); } if (c.Font != topControl.Font) { c.Font = new Font(referenceFont, c.Font.Style); } } }  
```  
  
 Con questo codice garantisce che, quando viene aggiornato il carattere del form, verrà aggiornato anche i tipi di carattere dei controlli. Questo metodo deve anche essere chiamato dal costruttore del form, perché la finestra di dialogo potrebbe non riuscire a ottenere un'istanza di **implementa IUIService** e **FontChanged** mai viene generato l'evento. Associazione **FontChanged** consentirà di finestre di dialogo prelevare dinamicamente il nuovo tipo di carattere, anche se la finestra di dialogo è già aperto.  
  
### Il tipo di carattere ambiente di test  
 Per assicurarsi che l'interfaccia utente utilizza il tipo di carattere ambiente e rispetta le impostazioni della dimensione, aprire **Strumenti \> Opzioni \> ambiente \> tipi di carattere e colori** selezionare "Tipo di carattere ambiente" i "Mostra impostazioni per:" menu a discesa.  
  
 ![Fonts and Colors page in Tools &#62; Options dialog](../../extensibility/ux-guidelines/media/0201-a_optionsfonts.png "0201\-a\_OptionsFonts")  
  
 **Le impostazioni di tipi di carattere e colori in Strumenti \> finestra di dialogo Opzioni**  
  
 Impostare il tipo di carattere in qualcosa di molto diverso da quello predefinito. Per rendere più ovvio che non determinano l'aggiornamento dell'interfaccia utente, scegliere un tipo di carattere con grazie \(ad esempio "Times New Roman"\) e impostare le dimensioni molto grandi. Quindi il test dell'interfaccia utente per garantire che rispetta l'ambiente. Di seguito è riportato un esempio con la finestra di dialogo di licenza:  
  
 ![Example of dialog not using the environment font](../../extensibility/ux-guidelines/media/0201-b_wrongfontdialog.png "0201\-b\_WrongFontDialog")  
  
 **Esempio di testo dell'interfaccia utente che non rispettano il tipo di carattere ambiente**  
  
 In questo caso, "Informazioni" e "Informazioni" sono non rispettano il tipo di carattere. In alcuni casi potrebbe trattarsi di una scelta di progettazione esplicite, ma può trattarsi di un bug, se il tipo di carattere esplicita non è specificato come parte delle specifiche con linea rossa.  
  
 Per reimpostare il tipo di carattere, fare clic su "Utilizza le impostazioni predefinite" in **Strumenti \> Opzioni \> ambiente \> tipi di carattere e colori**.  
  
##  <a name="BKMK_TextStyle"></a> Stile del testo  
 Lo stile del testo si riferisce a maiuscole e minuscole, lo spessore e la dimensione del carattere. Per indicazioni di implementazione, vedere [Il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
### Testo maiuscolo  
  
#### Maiuscole  
 Non utilizzare maiuscole per i titoli o le etichette in Visual Studio.  
  
#### Tutte le lettere minuscole  
 Non utilizzare tutte lettere minuscole per i titoli o le etichette in Visual Studio.  
  
#### Caso frase e il titolo  
 Testo in Visual Studio deve utilizzare maiuscole o minuscole frase, a seconda della situazione.  
  
|Utilizzare maiuscole per:|Frase caso di utilizzo:|  
|-------------------------------|-----------------------------|  
|Titoli di finestra di dialogo|Etichette|  
|Caselle di gruppo|Caselle di controllo|  
|Voci di menu|Pulsanti di opzione|  
|Voci del menu contestuale|Voci elenco|  
|Pulsanti|Barre di stato|  
|In una tabella pivot||  
|Intestazioni di colonna||  
|Descrizioni comandi||  
  
##### Iniziali maiuscole  
 Iniziali maiuscole sono uno stile in cui sono in maiuscolo le prime lettere della maggior parte o tutte le parole all'interno di una frase. In Visual Studio, maiuscole viene utilizzata per molti elementi, tra cui:  
  
-   **Descrizioni comandi.** Esempio: "anteprima di elementi selezionati"  
  
-   **Intestazioni di colonna.** Esempio: "risposta di sistema"  
  
-   **Voci di menu.** Esempio: "Salva tutto"  
  
 Quando si utilizza iniziali maiuscole, queste sono le linee guida per quando sfruttare al meglio le parole e lasciare le lettere minuscole:  
  
|Maiuscole|Esempi e commenti|  
|---------------|-----------------------|  
|Tutti i sostantivi||  
|Tutti i verbi|Tra cui altre forme di "per essere" e "È"|  
|Adverb tutti|Tra cui "Di" e "When"|  
|Tutti gli aggettivi|Tra cui "This" e "Che"|  
|Tutti i pronomi|Tra cui l'impropri "Relativo" anche come "È", una contrazione del Pronome "it" e il verbo "is"|  
|Parole e il cognome, indipendentemente dalle parti del discorso||  
|Preposizioni che fanno parte di una frase verbo|"La chiusura di tutti i Windows" o "Arresto del sistema"|  
|Tutte le lettere di un acronimo|HTML, XML, URL, IDE, RGB|  
|La seconda parola in una parola composta se è un o aggettivali corretto o se le parole hanno lo stesso peso|Riferimento incrociato, Software, pre\-Microsoft accesso di lettura\/scrittura, in fase di esecuzione|  
  
|Minuscole|Esempi|  
|---------------|------------|  
|La seconda parola in una parola composta se si tratta di un'altra parte del discorso o una participio modifica la prima parola|E le procedure, decollo|  
|Articoli, a meno che uno è la prima parola nel titolo|un oggetto, un oggetto, il|  
|Coordinare congiunzioni|e, invece, né, o|  
|Preposizioni con parole di un massimo di quattro lettere di fuori di una frase verbo|in, in, come per fuori, nella parte superiore di|  
|"A" utilizzato in una frase infinita|"Come formattare il disco rigido"|  
  
##### Normale  
 Frase normale è il metodo di lettere maiuscole\/minuscole standard per la scrittura in cui è in maiuscolo la prima parola della frase, insieme a eventuali nomi propri e il Pronome "I". In generale, caso di frase è più facile per utenti internazionali per la lettura, soprattutto quando il contenuto verrà convertito da una macchina. Frase caso di utilizzo:  
  
1.  **Messaggi della barra di stato.** Queste sono semplici, breve e fornire solo informazioni sullo stato. Esempio: "caricamento file di progetto"  
  
2.  **Tutti gli altri elementi dell'interfaccia utente**, tra cui le etichette, caselle di controllo, pulsanti di opzione ed elencare gli elementi della casella. Esempio: "Seleziona tutti gli elementi nell'elenco"  
  
### Formattazione del testo  
 Formattazione predefinita in Visual Studio 2013 è controllato da un [Il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont). Questo servizio consente di garantire un aspetto coerente del carattere nel corso dell'IDE \(integrated development environment\) e deve essere utilizzata per garantire un'esperienza coerente per gli utenti.  
  
 La dimensione predefinita utilizzata dal servizio di tipo di carattere di Visual Studio viene fornito da Windows e viene visualizzata come 9 punti.  
  
 È possibile applicare la formattazione per il tipo di carattere ambiente. In questo argomento viene illustrato come e dove utilizzare stili. Per informazioni sull'implementazione, vedere [Il tipo di carattere ambiente](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
#### Testo in grassetto  
 Testo in grassetto è utilizzato con cautela in Visual Studio e deve essere riservato per:  
  
-   etichette domanda nelle procedure guidate  
  
-   che designa il progetto attivo in Esplora soluzioni  
  
-   valori sottoposti a override nella finestra degli strumenti proprietà  
  
-   alcuni eventi negli elenchi a discesa editor di Visual Basic  
  
-   contenuto generato dal server nella struttura del documento per le pagine web  
  
-   intestazioni di sezione nella finestra di dialogo complesso o di progettazione dell'interfaccia utente  
  
#### Corsivo  
 Visual Studio non viene utilizzato testo in corsivo corsivo o in grassetto.  
  
#### Colore  
  
-   Blu è riservato per i collegamenti ipertestuali \(spostamento e l'esecuzione di comandi\) e non deve mai essere utilizzato per l'orientamento.  
  
-   Per questi scopi, è possono colorare le intestazioni di dimensioni maggiori \(tipo di carattere ambiente 155% o superiore\):  
  
    -   Per fornire l'impatto visivo alla firma dell'interfaccia utente di Visual Studio  
  
    -   Per richiamare l'attenzione su un'area specifica  
  
    -   Per offrire scarico dal colore del testo standard ambiente\/nero grigio scuro  
  
-   Colore delle intestazioni deve utilizzare Visual Studio marchio colori esistenti, principalmente viola principale, FF68217A \#.  
  
-   Quando si utilizza colore nelle intestazioni, è necessario rispettare il [Windows colore linee guida](https://msdn.microsoft.com/en-us/library/dn742482.aspx), tra cui contrasto e altre considerazioni sull'accesso facilitato.  
  
### Dimensione carattere  
 Progettazione di Visual Studio dell'interfaccia utente è dotato di un aspetto più chiaro con più spazi. Dove possibile, le barre di colore e il titolo sono stati ridotte o rimosse. Mentre densità di informazioni è un requisito in Visual Studio, tipografia continua a essere importante, con un'enfasi su interlinea più aperto e una variante di pesi e le dimensioni dei caratteri.  
  
 Nelle tabelle seguenti sono inclusi dettagli della progettazione ed esempi visivi per i caratteri utilizzati in Visual Studio. Alcune variazioni di carattere visualizzazione abbiano sia le dimensioni e peso, ad esempio Semilight o luce, codificate il loro aspetto.  
  
 Frammenti di codice di implementazione per la visualizzazione di tutti i tipi di carattere sono reperibili in [Formattazione di riferimento (scalabilità/formattazione in grassetto)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_Formatting).  
  
#### Tipo di carattere ambiente 375% \+ Light  
  
|||  
|-|-|  
|**Utilizzo:** rari. Univoco personalizzata dell'interfaccia utente solo.<br /><br /> **Eseguire:**<br /><br /> -   Frase caso di utilizzo<br />-   Utilizzare sempre Light weight<br /><br /> **Non:**<br /><br /> -   Utilizzare per l'interfaccia utente invece di firma dell'interfaccia utente, ad esempio pagina iniziale<br />-   Grassetto, corsivo o grassetto, corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** pt 34 Segoe UI Light<br /><br /> **Esempio visivo:**<br /><br /> *Attualmente non usato. Possono essere utilizzati nella pagina iniziale.*|  
  
#### Tipo di carattere ambiente 310% \+ Light  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -   Intestazione di dimensioni maggiori nelle finestre di dialogo firma<br />-   Intestazione di report principale<br /><br /> **Eseguire:**<br /><br /> -   Frase caso di utilizzo<br />-   Utilizzare sempre Light weight<br /><br /> **Non:**<br /><br /> -   Utilizzare per l'interfaccia utente invece di firma dell'interfaccia utente, ad esempio pagina iniziale<br />-   Grassetto, corsivo o grassetto, corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** pt 28 Segoe UI Light<br /><br /> **Esempio visivo:**<br /><br /> ![Example of 310% Environment font &#43; Light heading](../../extensibility/ux-guidelines/media/0202-a_ef310.png "0202\-a\_EF310")|  
  
#### Tipo di carattere ambiente 200% \+ Semilight  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -   Sottotitoli<br />-   Titoli di finestre di dialogo di piccole e medie dimensioni<br /><br /> **Eseguire:**<br /><br /> -   Frase caso di utilizzo<br />-   Utilizzare sempre peso Semilight<br /><br /> **Non:**<br /><br /> -   Grassetto, corsivo o grassetto, corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** 18 pt Segoe UI Semillight<br /><br /> **Esempio visivo:**<br /><br /> ![Example of 200% Environment font &#43; Semilight](../../extensibility/ux-guidelines/media/0202-b_ef200.png "0202\-b\_EF200")|  
  
#### Tipo di carattere ambiente 155%  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -   Intestazioni di sezione nel documento e dell'interfaccia utente<br />-   Report<br /><br /> **Si:** frase caso di utilizzo<br /><br /> **Non:**<br /><br /> -   Grassetto, corsivo o grassetto, corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare in Visual Studio i controlli standard<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** 14 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Example of 155% Environment font heading](../../extensibility/ux-guidelines/media/0202-c_ef155.png "0202\-c\_EF155")|  
  
#### Tipo di carattere ambiente 133%  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -   Sezioni più piccole nelle finestre di dialogo firma<br />-   Sottotitoli inferiori nel documento e dell'interfaccia utente<br /><br /> **Si:** frase caso di utilizzo<br /><br /> **Non:**<br /><br /> -   Grassetto, corsivo o grassetto, corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare in Visual Studio i controlli standard<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** 12 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Example of 133% Environment font heading](../../extensibility/ux-guidelines/media/0202-d_ef133.png "0202\-d\_EF133")|  
  
#### Tipo di carattere ambiente 122%  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -   Intestazioni di sezione nelle finestre di dialogo firma<br />-   Nodi principali nella visualizzazione ad albero<br />-   Spostamento di tabulazione verticale<br /><br /> **Si:** frase caso di utilizzo<br /><br /> **Non:**<br /><br /> -   Grassetto, corsivo o grassetto, corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare in Visual Studio i controlli standard<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** 11 pt Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Example of 122% Environment font heading](../../extensibility/ux-guidelines/media/0202-e_ef122.png "0202\-e\_EF122")|  
  
#### Tipo di carattere ambiente \+ grassetto  
  
|||  
|-|-|  
|**Utilizzo:**<br /><br /> -   Le etichette e i sottotitoli nelle finestre di dialogo firma<br />-   Le etichette e i sottotitoli nei report<br />-   Le etichette e i sottotitoli nel documento e dell'interfaccia utente<br /><br /> **Eseguire:**<br /><br /> -   Frase caso di utilizzo<br />-   Utilizzare spessore grassetto<br /><br /> **Non:**<br /><br /> -   Corsivo grassetto o corsivo<br />-   Utilizzare per il corpo del testo<br />-   Utilizzare in Visual Studio i controlli standard<br />-   Utilizzare nelle finestre degli strumenti|**Viene visualizzato come:** in grassetto 9 punti Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Example of Environment font &#43; Bold heading](../../extensibility/ux-guidelines/media/0202-f_efb.png "0202\-f\_EFB")|  
  
#### Tipo di carattere ambiente  
  
|||  
|-|-|  
|**Utilizzo:** tutto il testo rimanente<br /><br /> **Si:** frase caso di utilizzo<br /><br /> **Non:** corsivo o grassetto corsivo|**Viene visualizzato come:** 9 punti Segoe UI<br /><br /> **Esempio visivo:**<br /><br /> ![Example of Environment font](../../extensibility/ux-guidelines/media/0202-g_ef.png "0202\-g\_EF")|  
  
### Spaziatura interna e la spaziatura  
 Intestazioni richiedono spazio attorno a esse per consentire l'enfasi appropriato. Questo spazio varia a seconda dimensione e cos'altro è vicino il titolo, ad esempio una regola orizzontale o una riga di testo nel tipo di carattere ambiente.  
  
-   La spaziatura interna ideale per un'intestazione di per sé deve essere 90% dello spazio di altezza caratteri maiuscoli. Ad esempio, un'intestazione di Segoe UI Light pt 28 ha un'altezza di perno di 26 pt e la spaziatura interna deve essere circa 23 punti o pixel circa 31.  
  
-   Lo spazio intorno a un'intestazione minimo pari al 50% dell'altezza del carattere capitale. Meno spazio può essere utilizzato quando un'intestazione è accompagnata da una regola o un altro elemento di una stretta adattamento.  
  
-   Testo con un carattere in grassetto ambiente deve seguire la spaziatura interna e spaziatura altezza riga predefinita.  
  
## Vedere anche  
 [MSDN: I tipi di carattere \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742483\(v=vs.85\).aspx)   
 [MSDN: Testo dell'interfaccia utente \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)