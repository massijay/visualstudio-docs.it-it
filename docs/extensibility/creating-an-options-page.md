---
title: "Creazione di una pagina di opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pagine Opzioni del menu Strumenti [Visual Studio SDK], creazione"
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
caps.latest.revision: 62
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 62
---
# Creazione di una pagina di opzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata crea una pagina Strumenti\/opzioni semplice che utilizza una griglia delle proprietà per esaminare e impostare le proprietà.  
  
 Per salvare le proprietà a e il ripristino da un file di impostazioni, eseguire la procedura seguente e quindi visualizzare [Creazione di una categoria di impostazioni](../extensibility/creating-a-settings-category.md).  
  
 Il MPF fornisce due classi che consentono di creare pagine delle opzioni del menu Strumenti, la <xref:Microsoft.VisualStudio.Shell.Package> classe e la <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Creare un VSPackage per fornire un contenitore per le pagine tramite sottoclassi di classe del pacchetto. Ogni pagina di opzioni degli strumenti create mediante derivazione dalla classe DialogPage.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di una pagina della griglia di opzioni strumenti  
 In questa sezione è creare una griglia delle proprietà opzioni degli strumenti semplice. Utilizzare questa griglia per visualizzare e modificare il valore di una proprietà.  
  
#### Per creare il progetto VSIX e aggiungere un VSPackage  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene le risorse di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyToolsOptionsExtension`. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  Aggiungere un VSPackage aggiungendo un modello di elemento di pacchetto di Visual Studio denominato `MyToolsOptionsPackage`. Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, visitare **elementi Visual c\# \/ Extensibility** e selezionare **pacchetto Visual Studio**. Nel **nome** campo nella parte inferiore della finestra di dialogo, modificare il nome di file in `MyToolsOptionsPackage.cs`. Per ulteriori informazioni su come creare un pacchetto Visual Studio, vedere [Creazione di un'estensione con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### Per creare la griglia delle proprietà Opzioni strumenti  
  
1.  Aprire il file MyToolsOptionsPackage nell'editor di codice.  
  
2.  Aggiungere la seguente istruzione using.  
  
    ```c#  
    using System.ComponentModel;  
    ```  
  
3.  Dichiarare una classe OptionPageGrid e derivare da <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Applicare un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage per assegnare una categoria di opzioni e il nome di pagina Opzioni per il OptionPageGrid alla classe. Il risultato dovrebbe essere simile al seguente:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Aggiungere un `OptionInteger` proprietà per la `OptionPageGrid` classe.  
  
    -   Applicare un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> da assegnare alla proprietà una categoria di proprietà della griglia.  
  
    -   Applicare un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> da assegnare alla proprietà un nome.  
  
    -   Applicare un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> da assegnare alla proprietà di una descrizione.  
  
    ```c#  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> supporta proprietà che dispongono di convertitori appropriati o che sono strutture o matrici che possono essere espansa in proprietà che dispongono di convertitori appropriati. Per un elenco dei convertitori di tipi, vedere il <xref:System.ComponentModel> dello spazio dei nomi.  
  
6.  Compilare il progetto e avviare il debug.  
  
7.  Nell'istanza sperimentale di Visual Studio, nel **strumenti** menu fare clic su **Opzioni**.  
  
     Nel riquadro a sinistra dovrebbe essere **categoria My**. \(Opzioni categorie sono elencate in ordine alfabetico, in modo che dovrebbe essere visualizzata sulla metà verso il basso l'elenco.\) Aprire **categoria My** e quindi fare clic su **pagina griglia personale**. Nel riquadro di destra viene visualizzata la griglia di opzioni. La categoria della proprietà è **opzioni personali**, e il nome della proprietà **opzione Integer My**. La descrizione della proprietà, **l'opzione intero**, viene visualizzata nella parte inferiore del riquadro. Modificare il valore dal valore iniziale pari a 256 per qualcos'altro. Fare clic su **OK**, e quindi riaprire **pagina griglia personale**. È possibile vedere che il nuovo valore viene mantenuto.  
  
     La pagina delle opzioni è disponibile anche tramite avvio veloce di Visual Studio. Nella finestra di avvio veloce nell'angolo superiore destro dell'IDE, digitare **categoria My** e verrà visualizzato **categoria personale \-\> pagina della griglia My** nell'elenco a discesa.  
  
## Creazione di un oggetto personalizzato di opzioni strumenti pagina  
 In questa sezione è creare una pagina di opzioni degli strumenti con un'interfaccia utente personalizzata. Utilizzare questa pagina per visualizzare e modificare il valore di una proprietà.  
  
1.  Aprire il file MyToolsOptionsPackage nell'editor di codice.  
  
2.  Aggiungere la seguente istruzione using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Aggiungere un `OptionPageCustom` classe poco prima che la `OptionPageGrid` classe. Derivare la nuova classe da `DialogPage`.  
  
    ```c#  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  Aggiungere un attributo GUID. Aggiungere una proprietà OptionString:  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  Applicare un secondo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage. Questo attributo assegna la classe di una categoria di opzioni e il nome di pagina di opzioni.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Aggiungere un nuovo **controllo utente** denominato MyUserControl al progetto.  
  
7.  Aggiungere un **TextBox** il controllo utente.  
  
     Nel **proprietà** finestra, sulla barra degli strumenti, fare clic su di **eventi** pulsante e quindi fare doppio clic su di **lasciare** evento. Il nuovo gestore eventi viene visualizzato nel codice MyUserControl.cs.  
  
8.  Aggiungere un componente pubblico `OptionsPage` campo, un `Initialize` metodo alla classe di controllo, e aggiorna il gestore dell'evento per impostare l'opzione valore in base al contenuto della casella di testo:  
  
    ```c#  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     Il `optionsPage` campo contiene un riferimento all'elemento padre `OptionPageCustom` istanza. Il `Initialize` metodo visualizza `OptionString` nel **TextBox**. Il gestore dell'evento scrive il valore corrente del **TextBox** per il `OptionString` concentrarsi quando lascia il **TextBox**.  
  
9. Nel file di codice del pacchetto, aggiungere una sostituzione per il `OptionPageCustom.Window` proprietà alla classe per creare, inizializzare e restituire un'istanza di OptionPageCustom `MyUserControl`. La classe dovrebbe essere simile al seguente:  
  
    ```c#  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Compilare ed eseguire il progetto.  
  
11. Nell'istanza sperimentale, fare clic su **Strumenti \/ opzioni**.  
  
12. Trovare **del nome della categoria** e quindi **personalizzato pagina**.  
  
13. Modificare il valore di **OptionString**. Fare clic su **OK**, e quindi riaprire **pagina personalizzata personale**. È possibile vedere che il nuovo valore ha reso persistente.  
  
## Accesso alle opzioni  
 In questa sezione ottenere il valore di un'opzione dal VSPackage che ospita la pagina di opzioni degli strumenti associata. La stessa tecnica può essere utilizzata per ottenere il valore di qualsiasi proprietà pubblica.  
  
1.  Nel file di codice del pacchetto, aggiungere una proprietà pubblica denominata **OptionInteger** per il **MyToolsOptionsPackage** \(classe\).  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Questo codice chiama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per creare o recuperare un `OptionPageGrid` istanza.`OptionPageGrid` chiamate <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> per caricare le relative opzioni, che sono proprietà pubbliche.  
  
2.  A questo punto aggiungere un modello di elemento di comando personalizzato denominato **MyToolsOptionsCommand** per visualizzare il valore. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c\# \/ Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **MyToolsOptionsCommand.cs**.  
  
3.  Nel file MyToolsOptionsCommand, sostituire il corpo del comando `ShowMessageBox` metodo con il codice seguente:  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compilare il progetto e avviare il debug.  
  
5.  Nell'istanza sperimentale, nel **Tools** menu, fare clic su **richiamare MyToolsOptionsCommand**.  
  
     Una finestra di messaggio Visualizza il valore corrente di `OptionInteger`.  
  
## Vedere anche  
 [Opzioni e le pagine di opzioni](../extensibility/internals/options-and-options-pages.md)