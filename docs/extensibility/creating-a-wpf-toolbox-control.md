---
title: "Creazione di un controllo casella degli strumenti WPF | Microsoft Docs"
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
  - "controllo della casella degli strumenti"
  - "casella degli strumenti"
  - "wpf"
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un controllo casella degli strumenti WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il modello di controllo della casella degli strumenti WPF \(Windows Presentation Framework\) consente di creare controlli WPF che vengono aggiunte automaticamente le **della casella degli strumenti** quando l'estensione viene installata. In questo argomento viene illustrato come utilizzare il modello per creare un **della casella degli strumenti** controllo che è possibile distribuire ad altri utenti.  
  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un controllo casella degli strumenti WPF  
  
#### Creare un'estensione con un controllo casella degli strumenti WPF  
  
1.  Creare un progetto VSIX denominato `MyToolboxControl`. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un **controllo casella degli strumenti WPF** il modello di elemento denominato `MyToolboxControl`. Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c\# \/ Extensibility** e selezionare **controllo casella degli strumenti WPF**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando per `MyToolboxControl.cs`.  
  
     La soluzione ora contiene un controllo utente, un `ProvideToolboxControlAttribute`<xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> che aggiunge il controllo per il **della casella degli strumenti**, e un **Microsoft.VisualStudio.ToolboxControl** voce della risorsa nel manifesto VSIX per la distribuzione.  
  
#### Creare l'interfaccia utente del controllo  
  
1.  Aprire MyToolboxControl.xaml nella finestra di progettazione.  
  
     La finestra di progettazione mostra un controllo <xref:System.Windows.Controls.Grid> che contiene un controllo <xref:System.Windows.Controls.Button>.  
  
2.  Modificare il layout di griglia. Quando si seleziona il <xref:System.Windows.Controls.Grid> di controllo, vengono visualizzate le barre di controllo blu sui bordi superiore e sinistro della griglia. È possibile aggiungere righe e colonne alla griglia facendo clic sulle barre.  
  
3.  Aggiungere i controlli figlio alla griglia. È possibile posizionare un controllo figlio trascinandolo dal **della casella degli strumenti** a una sezione della griglia, oppure impostando il relativo `Grid.Row` e `Grid.Column` attributi in XAML. Nell'esempio seguente aggiunge due etichette nella parte superiore della griglia e un pulsante nella seconda riga.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## Ridenominazione del controllo  
 Per impostazione predefinita, il controllo verrà visualizzato nel **della casella degli strumenti** come **MyToolboxControl** in un gruppo denominato **MyToolboxControl.MyToolboxControl**. È possibile modificare questi nomi nel file MyToolboxControl.xaml.cs.  
  
1.  Aprire MyToolboxControl.xaml.cs nella visualizzazione codice.  
  
2.  Individuare la classe MyToolboxControl e rinominarlo TestControl. \(Il modo più rapido per eseguire questa operazione consiste nel rinominare la classe, quindi selezionare **rinominare** dal menu di scelta rapida e completare i passaggi. \(Per ulteriori informazioni sui **rinominare** comando, vedere [Refactoring di ridenominazione \(C\#\)](../csharp-ide/rename-refactoring-csharp.md).\)  
  
3.  Andare alla `ProvideToolboxControl` dell'attributo e modificare il valore del primo parametro per **Test**. Si tratta del nome del gruppo che conterrà il controllo di **della casella degli strumenti**.  
  
     Il codice risultante dovrebbe essere simile al seguente:  
  
    ```c#  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## Compilazione, testing e distribuzione  
 Quando si esegue il debug del progetto, è necessario trovare il controllo installato nel **della casella degli strumenti** dell'istanza sperimentale di Visual Studio.  
  
#### Per compilare e testare il controllo  
  
1.  Ricompilare il progetto e avviare il debug.  
  
2.  Nella nuova istanza di Visual Studio creare un progetto di applicazione WPF. Assicurarsi che la finestra di progettazione XAML sia aperto.  
  
3.  Individuare il controllo nella **casella degli strumenti** e trascinarlo nell'area di progettazione.  
  
4.  Avviare il debug dell'applicazione WPF.  
  
5.  Verificare che il controllo venga visualizzato.  
  
#### Per distribuire il controllo  
  
1.  Dopo aver compilato il progetto di test, è possibile trovare il file. VSIX nella cartella \\bin\\debug\\ del progetto.  
  
2.  È possibile installare in un computer locale facendo doppio clic sul file VSIX e seguendo la procedura di installazione. Per disinstallare il controllo, andare a **Strumenti \/ estensioni e aggiornamenti** e cercare l'estensione del controllo, quindi fare clic su **Disinstalla**.  
  
3.  Caricare il file VSIX in una rete o in un sito Web.  
  
     Se si carica il file di [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web, è possono utilizzare altri utenti **Strumenti \/ estensioni e aggiornamenti** in Visual Studio per trovare il controllo online e installarlo.