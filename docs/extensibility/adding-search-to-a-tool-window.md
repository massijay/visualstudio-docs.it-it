---
title: Aggiunta di ricerca a una finestra degli strumenti | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: bca8c87d4f7d89d491fab13e1a511febce81d3d8
ms.openlocfilehash: 845bbc5c34280f7ceafcaa3d763065f6d73388fe
ms.lasthandoff: 02/22/2017

---
# <a name="adding-search-to-a-tool-window"></a>Aggiunta di ricerca a una finestra degli strumenti
Quando si crea o aggiorna una finestra degli strumenti nell'estensione, è possibile aggiungere la stessa funzionalità di ricerca che viene visualizzato in un' posizione in Visual Studio. Questa funzionalità include le funzionalità seguenti:  
  
-   Una casella di ricerca che si trova sempre in un'area della barra degli strumenti personalizzata.  
  
-   Indicatore di stato che è visibile la casella di ricerca.  
  
-   La possibilità di visualizzare i risultati non appena si immette ogni carattere (ricerca immediata) o solo dopo aver premuto il tasto INVIO (ricerca su richiesta).  
  
-   Un elenco contenente le condizioni per cui avere cercato più di recente.  
  
-   La possibilità di filtrare le ricerche per gli aspetti delle destinazioni di ricerca o campi specifici.  
  
 Seguendo questa procedura dettagliata, si apprenderà come eseguire le attività seguenti:  
  
1.  Creare un progetto VSPackage.  
  
2.  Creare una finestra degli strumenti contenente un controllo utente con una casella di testo di sola lettura.  
  
3.  Aggiungere una casella di ricerca alla finestra dello strumento.  
  
4.  Aggiungere l'implementazione della ricerca.  
  
5.  Abilitare la funzionalità Ricerca immediata e la visualizzazione di un indicatore di stato.  
  
6.  Aggiungere un **maiuscole/minuscole** (opzione).  
  
7.  Aggiungere un **cercare solo le righe anche** filtro.  
  
## <a name="to-create-a-vsix-project"></a>Per creare un progetto VSIX  
  
1.  Creare un progetto VSIX denominato `TestToolWindowSearch` con una finestra degli strumenti denominata **TestSearch**. Per assistenza durante questa operazione, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Per creare una finestra degli strumenti  
  
1.  Nel `TestToolWindowSearch` del progetto, aprire il file TestSearchControl.xaml.  
  
2.  Sostituire il `<StackPanel>` blocco con il blocco seguente, che aggiunge una proprietà di sola lettura <xref:System.Windows.Controls.TextBox>per il <xref:System.Windows.Controls.UserControl>nella finestra degli strumenti.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.Controls.TextBox>  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  Nel file TestSearchControl.xaml.cs, aggiungere la seguente istruzione using:  
  
    ```c#  
    using System.Text;  
    ```  
  
4.  Rimuovere il `button1_Click()` metodo.  
  
     Nel **TestSearchControl** classe, aggiungere il codice seguente.  
  
     Questo codice viene aggiunto a un pubblico <xref:System.Windows.Controls.TextBox>proprietà denominata **SearchResultsTextBox** e una proprietà pubblica denominata **SearchContent**.</xref:System.Windows.Controls.TextBox> Nel costruttore, SearchResultsTextBox è impostata su casella di testo e SearchContent viene inizializzata su un set di stringhe delimitato da carattere di nuova riga. Il contenuto della casella di testo viene inoltre inizializzato al set di stringhe.  
  
    ```c#  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-cs[N.&1; ToolWindowSearch](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs) ] 
     [!code-vb [ToolWindowSearch n.&1;](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale di Visual Studio.  
  
6.  Nella barra dei menu, scegliere **visualizzazione**, **altre finestre**, **TestSearch**.  
  
     Verrà visualizzata la finestra degli strumenti, ma non viene ancora visualizzato il controllo di ricerca.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Per aggiungere una casella di ricerca sulla finestra degli strumenti  
  
1.  Nel file TestSearch.cs, aggiungere il codice seguente per la `TestSearch` classe. Il codice esegue l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>proprietà in modo che la funzione di accesso get restituisce `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>  
  
     Per attivare la ricerca, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>proprietà.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> Il <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>e fornisce un'implementazione predefinita che non consentono la ricerca.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> </xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
    ```c#  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
3.  Nell'istanza sperimentale di Visual Studio, aprire **TestSearch**.  
  
     Nella parte superiore della finestra degli strumenti, verrà visualizzato un controllo di ricerca con un **ricerca** filigrana e un'icona sulla lente di ingrandimento. Tuttavia, la ricerca non funziona ancora perché non è stato implementato il processo di ricerca.  
  
## <a name="to-add-the-search-implementation"></a>Per aggiungere l'implementazione della ricerca  
 Quando si attiva la ricerca in un <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, come nella procedura precedente, la finestra degli strumenti crea un host search.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> L'host imposta e gestisce i processi di ricerca, vengono eseguite sempre in un thread in background. Poiché la <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>classe gestisce la creazione di host di ricerca e l'impostazione di backup della ricerca, è necessario solo creare un'attività di ricerca e fornire il metodo search.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Si verifica il processo di ricerca in un thread in background e chiamate al controllo di finestra strumento avvengono nel thread dell'interfaccia utente. Pertanto, è necessario utilizzare il <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>metodo per gestire tutte le chiamate effettuate a gestire il controllo.</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
1.  Aggiungere il codice seguente nel file TestSearch.cs `using` istruzioni:  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  Nella `TestSearch` classe, aggiungere il codice seguente, che esegue le azioni seguenti:  
  
    -   Esegue l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>metodo per creare un'attività di ricerca.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch>  
  
    -   Esegue l'override di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>metodo per ripristinare lo stato della casella di testo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> Questo metodo viene chiamato quando un utente annulla un'operazione di ricerca e quando un utente imposta o annullata l'impostazione di opzioni o filtri. Entrambi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>chiamato sul thread UI.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> Pertanto, non è necessario accedere alla casella di testo tramite il <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>  
  
    -   Crea una classe denominata `TestSearchTask` che eredita da <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, che fornisce un'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> </xref:Microsoft.VisualStudio.Shell.VsSearchTask>  
  
         In `TestSearchTask`, il costruttore imposta un campo privato che fa riferimento la finestra degli strumenti. Per fornire il metodo di ricerca, si esegue l'override di <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>e <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>metodi.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> </xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Il <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>consiste in cui si implementa il processo di ricerca.</xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Questo processo include la ricerca, la visualizzazione dei risultati di ricerca nella casella di testo e chiama l'implementazione della classe di base di questo metodo per segnalare che la ricerca è stata completata.  
  
    ```c#  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Testare l'implementazione di ricerca attenendosi alla procedura seguente:  
  
    1.  Ricompilare il progetto e avviare il debug.  
  
    2.  Nell'istanza sperimentale di Visual Studio, aprire nuovamente la finestra degli strumenti, immettere un testo di ricerca nella finestra di ricerca e quindi premere INVIO.  
  
         I risultati corretti visualizzata.  
  
## <a name="to-customize-the-search-behavior"></a>Per personalizzare il comportamento di ricerca  
 Modificando le impostazioni di ricerca, è possibile rendere un'ampia gamma di modifiche nell'aspetto del controllo di ricerca e come viene eseguita la ricerca. Ad esempio, è possibile modificare la filigrana (il testo predefinito visualizzato nella casella di ricerca), il valore minimo e massima larghezza del controllo di ricerca e se si desidera visualizzare un indicatore di stato. È inoltre possibile modificare il punto di avviare i risultati della ricerca da visualizzare (su richiesta o ricerca immediata) e se si desidera visualizzare un elenco di termini per il quale recentemente eseguita la ricerca. È possibile trovare l'elenco completo delle impostazioni nella <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>classe.</xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>  
  
1.  Nel file TestSearch.cs, aggiungere il codice seguente per la `TestSearch` classe. Questo codice consente la ricerca immediata invece della ricerca su richiesta (che indica che l'utente non è necessario fare clic su invio). Il codice esegue l'override di `ProvideSearchSettings` metodo la `TestSearch` classe, è necessario modificare le impostazioni predefinite.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testare la nuova impostazione tramite la ricompilazione della soluzione e riavviare il debugger.  
  
     Risultati della ricerca visualizzata ogni volta che si immette un carattere nella casella di ricerca.  
  
3.  Nel `ProvideSearchSettings` (metodo), aggiungere la riga seguente, che consente di visualizzare un indicatore di stato.  
  
    ```c#  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     Per l'indicatore di stato vengono visualizzati, lo stato di avanzamento debba essere segnalato. Per segnalare lo stato di avanzamento, rimuovere il commento il codice seguente nel `OnStartSearch` metodo la `TestSearchTask` classe:  
  
    ```c#  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Rallentare l'elaborazione sufficiente che lo stato di avanzamento barra è visibile, rimuovere il commento la riga seguente nel `OnStartSearch` metodo la `TestSearchTask` classe:  
  
    ```c#  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Testare le nuove impostazioni di ricompilare la soluzione e iniziare a debugb.  
  
     L'indicatore di stato viene visualizzata nella finestra di ricerca (come una linea blu sotto la casella di testo di ricerca) ogni volta che si esegue una ricerca.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Per consentire agli utenti di eseguire ricerche selettive  
 È possibile consentire agli utenti di eseguire ricerche selettive tramite opzioni, ad esempio **maiuscole/minuscole** o **parole intere**. Opzioni possono essere booleane, che vengono visualizzati come caselle di controllo o i comandi che vengono visualizzati come pulsanti. Per questa procedura dettagliata, si creerà un'opzione booleana.  
  
1.  Nel file TestSearch.cs, aggiungere il codice seguente per la `TestSearch` classe. Il codice esegue l'override di `SearchOptionsEnum` metodo, che consente l'implementazione della ricerca rilevare se una determinata opzione è attivata o disattivata. Il codice in `SearchOptionsEnum` viene aggiunta un'opzione maiuscole / minuscole per un <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>enumeratore.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> L'opzione maiuscole / minuscole è disponibile anche come il `MatchCaseOption` proprietà.  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  Nel `TestSearchTask` (classe), rimuovere il commento riga maiuscole/minuscole di `OnStartSearch` metodo:  
  
    ```c#  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
         {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
3.  L'opzione di test:  
  
    1.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
    2.  Nella finestra degli strumenti, scegliere la freccia in giù a destra della casella di testo.  
  
         Il **maiuscole/minuscole** casella di controllo.  
  
    3.  Selezionare il **maiuscole/minuscole** casella di controllo e quindi eseguire alcune ricerche.  
  
## <a name="to-add-a-search-filter"></a>Per aggiungere un filtro di ricerca  
 È possibile aggiungere filtri di ricerca che consentono agli utenti rifinire il set di destinazioni di ricerca. Ad esempio, è possibile filtrare i file in Esplora File per le estensioni di nomi di file e le date in cui sono stati modificati più di recente. In questa procedura dettagliata, è necessario aggiungere un filtro anche solo per le righe. Quando l'utente sceglie il filtro, l'host di ricerca aggiunge le stringhe specificate per la query di ricerca. È quindi possibile identificare queste stringhe all'interno del metodo di ricerca e filtro di conseguenza gli obiettivi di ricerca.  
  
1.  Nel file TestSearch.cs, aggiungere il codice seguente per la `TestSearch` classe. Il codice implementa `SearchFiltersEnum` aggiungendo un <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>che specifica per filtrare i risultati della ricerca in modo che vengano visualizzate solo le righe pari.</xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>  
  
    ```c#  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     A questo punto il controllo di ricerca viene visualizzato il filtro di ricerca `Search even lines only`. Quando l'utente sceglie il filtro, la stringa `lines:"even"` viene visualizzato nella casella di ricerca. Altri criteri di ricerca possono essere visualizzati contemporaneamente come filtro. Stringhe di ricerca può essere visualizzato prima il filtro, dopo il filtro o entrambi.  
  
2.  Nel file TestSearch.cs, aggiungere i metodi seguenti per il `TestSearchTask` classe, che si trova il `TestSearch` (classe). Questi metodi supportano il `OnStartSearch` (metodo), che verrà modificato nel passaggio successivo.  
  
    ```c#  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  Nel `TestSearchTask` classe, aggiornare il `OnStartSearch` metodo con il codice seguente. Questa modifica aggiorna il codice per supportare il filtro.  
  
    ```c#  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Testare il codice.  
  
5.  Compilare il progetto e avviare il debug. Nell'istanza sperimentale di Visual Studio, aprire la finestra degli strumenti e quindi scegliere la freccia in giù del controllo di ricerca.  
  
     Il **maiuscole/minuscole** casella di controllo e il **cercare solo le righe anche** filtro visualizzato.  
  
6.  Scegliere il filtro.  
  
     La casella di ricerca contiene **righe: "anche"**, e vengono visualizzati i risultati seguenti:  
  
     buona&2;  
  
     4 buona  
  
     Addio&6;  
  
7.  Eliminare `lines:"even"` dalla casella di ricerca, selezionare il **maiuscole/minuscole** casella di controllo e quindi immettere `g` nella casella di ricerca.  
  
     Vengono visualizzati i risultati seguenti:  
  
     passare a&1;  
  
     buona&2;  
  
     Addio&5;  
  
8.  Scegliere la X sul lato destro della casella di ricerca.  
  
     La ricerca viene cancellata e il contenuto originale viene visualizzato. Tuttavia, il **maiuscole/minuscole** sia ancora selezionata.
