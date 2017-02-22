---
title: "Supporto per i frammenti di codice in un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "frammenti di codice, supporto in servizi di linguaggio"
  - "frammenti di codice, supporto in servizi di linguaggio [framework pacchetto gestito]"
  - "servizi di linguaggio [framework gestito pacchetto], supporto di frammenti di codice"
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Supporto per i frammenti di codice in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un frammento di codice è un frammento di codice che viene inserito nel file di origine. Il frammento stesso è un modello basato su XML con un set di campi. Questi campi vengono evidenziati dopo il frammento di codice viene inserito e può presentare valori diversi a seconda del contesto in cui viene inserito il frammento di codice. Immediatamente dopo l'inserimento del frammento, il servizio di linguaggio possibile formattare il frammento di codice.  
  
 Il frammento di codice viene inserito in una modalità di modifica speciale che consente i campi del frammento per spostarsi utilizzando il tasto TAB. I campi possono supportare i menu di IntelliSense in stile elenco a discesa. L'utente esegue il commit nel frammento di file di origine digitando l'invio o ESC. Per ulteriori informazioni sui frammenti di codice, vedere [Frammenti di codice](../../ide/code-snippets.md).  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Procedura dettagliata: Implementazione di frammenti di codice](../../extensibility/walkthrough-implementing-code-snippets.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Supporto per il Framework di frammenti di codice gestito  
 Il framework di pacchetto gestito \(MPF\) supporta la maggior parte delle funzionalità dei frammenti, di leggere il modello di inserimento del frammento e consentendo speciale modalità di modifica. Il supporto viene gestito tramite la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe.  
  
 Quando il <xref:Microsoft.VisualStudio.Package.Source> viene creata un'istanza di classe, il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe viene chiamata per ottenere un <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto \(si noti che la base <xref:Microsoft.VisualStudio.Package.LanguageService> classe restituisce sempre un nuovo <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto per ogni <xref:Microsoft.VisualStudio.Package.Source> oggetto\).  
  
 Il MPF non supporta le funzioni di espansione. Una funzione di espansione è una funzione denominata che è incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. I valori vengono restituiti dal linguaggio del servizio tramite un <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto. Il <xref:Microsoft.VisualStudio.Package.ExpansionFunction> oggetto deve essere implementato dal servizio di linguaggio per supportare le funzioni di espansione.  
  
## Fornisce supporto per i frammenti di codice  
 Per abilitare il supporto per i frammenti di codice, è necessario fornire o installare i frammenti di codice ed è necessario fornire i mezzi per l'utente di inserire i frammenti di codice. Esistono tre passaggi per abilitare il supporto per i frammenti di codice:  
  
1.  L'installazione dei file di frammento di codice.  
  
2.  Abilitazione di frammenti di codice per il servizio di linguaggio.  
  
3.  Richiamo di <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto.  
  
### L'installazione dei file di frammento di codice  
 Tutti i frammenti per una lingua vengono archiviati come modelli in file XML, in genere un modello di frammento di codice per ciascun file. Per ulteriori informazioni sullo schema XML utilizzato per modelli di frammenti di codice, vedere [Riferimento dello schema dei frammenti di codice](../../ide/code-snippets-schema-reference.md). Ogni modello di frammento di codice viene identificato con un ID di lingua. Questo linguaggio ID viene specificato nel Registro di sistema e viene inserito il `Language` attributo del tag \< codice \> nel modello.  
  
 In genere esistono due percorsi in cui sono archiviati i file di modello di frammento: 1\) in cui è stato installato il linguaggio e 2\) nella cartella dell'utente. Questi percorsi vengono aggiunti al Registro di sistema in modo che Visual Studio **Gestione frammenti di codice** possibile trovare i frammenti di codice. La cartella dell'utente è in cui sono archiviati i frammenti di codice creati dall'utente.  
  
 Il layout tipico cartella per i file di modello installato frammento di codice è simile al seguente: *\[InstallRoot\]*\\*\[TestLanguage\]*\\Snippets\\*\[LCID\]*\\snippets..  
  
 *\[InstallRoot\]* è la cartella del linguaggio è installato in.  
  
 *\[TestLanguage\]* è il nome della lingua come un nome di cartella.  
  
 *\[LCID\]* è l'ID impostazioni locali. Si tratta di versioni localizzate come frammenti di codice vengono archiviate. Ad esempio, l'ID impostazioni locali per l'inglese è 1033, pertanto *\[LCID\]* viene sostituito da 1033.  
  
 È necessario specificare un file aggiuntivo di un file di indice, in genere denominato SnippetsIndex.xml o ExpansionsIndex.xml \(è possibile utilizzare qualsiasi nome di file valido con estensione XML\). Questo file è in genere archiviato nel *\[InstallRoot\]*\\*\[TestLanguage\]* cartella e specifica la posizione esatta della cartella frammenti di codice, nonché l'ID lingua e il GUID del servizio di linguaggio che utilizza i frammenti di codice. Il percorso esatto del file di indice viene inserito nel Registro di sistema come descritto più avanti in "Installazione di voci del Registro di sistema". Di seguito è riportato un esempio di un file SnippetsIndex.xml:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 Il tag \< lingua \> specifica l'ID lingua \(il `Lang` attributo\) e il GUID del servizio di linguaggio.  
  
 In questo esempio si presuppone che è stato installato il servizio di linguaggio nella cartella di installazione di Visual Studio. La variabile % LCID % viene sostituita con l'ID impostazioni locali correnti. dell'utente Più tag \< SnippetDir \> possono essere aggiunti, uno per ogni altra directory e delle impostazioni locali. Inoltre, una cartella di frammento può contenere le sottocartelle, ognuna delle quali è identificato nel file di indice con il tag \< SnippetSubDir \> che viene incorporato in un tag \< SnippetDir \>.  
  
 Gli utenti possono inoltre creare i propri frammenti di codice per la propria lingua. Questi sono in genere archiviati nella cartella delle impostazioni dell'utente, ad esempio *\[TestDocs\]*\\Code Snippets\\*\[TestLanguage\]*\\Test frammenti di codice, in cui *\[TestDocs\]* è il percorso della cartella di impostazioni dell'utente di Visual Studio.  
  
 I seguenti elementi di sostituzione possono essere inseriti nel percorso memorizzato nel tag \< DirPath \> nel file di indice.  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|% LCID %|ID impostazioni locali.|  
|% InstallRoot %|Cartella di installazione principale di Visual Studio, ad esempio, C:\\Program Files\\Microsoft Visual Studio 8.|  
|% ProjDir %|Cartella contenente il progetto corrente.|  
|% ProjItem %|Cartella contenente l'elemento del progetto corrente.|  
|% TestDocs %|Nella cartella di impostazioni dell'utente, ad esempio, C:\\Documents and Settings \\*\[username\]*Documents\\Visual Studio\\8.|  
  
### Abilitazione di frammenti di codice per il servizio di linguaggio  
 È possibile abilitare i frammenti di codice per il servizio di linguaggio aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> attributo per il pacchetto Visual Studio \(vedere [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate\). Il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> e <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> i parametri sono facoltativi, ma è necessario includere il `SearchPaths` parametro denominato per informare il **Gestione frammenti di codice** il percorso dei frammenti di codice.  
  
 Di seguito è riportato un esempio di come utilizzare questo attributo:  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### Chiamare il Provider di espansione  
 Il servizio di linguaggio determina l'inserimento di ogni frammento di codice, nonché la modalità di inserimento viene richiamato.  
  
## Chiamare il Provider di espansione per frammenti di codice  
 Per richiamare il provider di espansione in due modi: utilizzando un comando di menu o utilizzando un collegamento da un elenco di completamento.  
  
### Inserimento di un frammento di codice tramite un comando di Menu  
 Per utilizzare un comando di menu per visualizzare il browser di frammento di codice, aggiungere un comando di menu e quindi chiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodo il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfaccia in risposta a tale voce di menu.  
  
1.  Aggiungere un comando e un pulsante al file vsct. È possibile trovare istruzioni per effettuare questa operazione nel [Procedura dettagliata: Creazione di un comando di menu tramite il modello di pacchetto di Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
2.  Derivare una classe dalla <xref:Microsoft.VisualStudio.Package.ViewFilter> classe ed eseguire l'override di <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodo per indicare il supporto per il nuovo comando di menu. In questo esempio consente sempre il comando di menu.  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  Eseguire l'override di <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> metodo nella <xref:Microsoft.VisualStudio.Package.ViewFilter> classe per ottenere il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto e chiamare il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodo sull'oggetto.  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     I metodi seguenti di <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe vengono chiamati nell'ordine specificato durante il processo di inserimento del frammento da Visual Studio:  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     Dopo il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> viene chiamato il metodo, è stato inserito il frammento di codice e <xref:Microsoft.VisualStudio.Package.ExpansionProvider> oggetto si trova in una modalità di modifica speciali utilizzate per la modifica di un frammento di codice appena inserito.  
  
### Inserimento di un frammento di codice tramite un collegamento  
 Implementazione di un collegamento da un elenco di completamento è molto più complessa rispetto all'implementazione di un comando di menu. È innanzitutto necessario aggiungere collegamenti dei frammenti all'elenco di completamento IntelliSense word. È quindi necessario rilevare quando un nome di scelta rapida del frammento di codice è stato inserito in seguito al completamento. Infine, è necessario ottenere il frammento di codice titolo e il percorso utilizzando il nome del collegamento e passare tali informazioni per il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo il <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metodo.  
  
 Per aggiungere collegamenti dei frammenti all'elenco di completamento di word, aggiungerli al <xref:Microsoft.VisualStudio.Package.Declarations> oggetto di <xref:Microsoft.VisualStudio.Package.AuthoringScope> \(classe\). È necessario assicurarsi che è possibile identificare il collegamento come un nome. Per un esempio, vedere [Procedura dettagliata: Ottenere un elenco di frammenti di codice installato \(implementazione Legacy\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
 È possibile rilevare l'inserimento di collegamento al frammento di codice nel <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metodo la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Poiché il nome del frammento di codice è già stato inserito nel file di origine, è necessario rimuoverlo quando viene inserito l'espansione. Il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo accetta un intervallo che descrive il punto di inserimento del frammento; se l'intervallo include il nome intero frammento di codice nel file di origine, tale nome viene sostituito con il frammento di codice.  
  
 Di seguito è una versione di un <xref:Microsoft.VisualStudio.Package.Declarations> che gestisce l'inserimento del frammento assegnato un nome di scelta rapida. Altri metodi di <xref:Microsoft.VisualStudio.Package.Declarations> classe sono stati omessi per maggiore chiarezza. Si noti che il costruttore di questa classe accetta un <xref:Microsoft.VisualStudio.Package.LanguageService> oggetto. Questo può essere passato dalla versione di <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto \(ad esempio, l'implementazione della <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe potrebbe richiedere il <xref:Microsoft.VisualStudio.Package.LanguageService> nel relativo costruttore, quindi passare tale oggetto al `TestDeclarations` costruttore della classe\).  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 Quando il servizio di linguaggio Ottiene il nome del collegamento, viene chiamato il <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> per ottenere il titolo del frammento filename e codice. Chiama quindi il servizio di linguaggio di <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metodo la <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe per inserire il frammento di codice. I seguenti metodi vengono chiamati da Visual Studio nell'ordine specificato nella <xref:Microsoft.VisualStudio.Package.ExpansionProvider> classe durante il processo di inserimento del frammento:  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 Per ulteriori informazioni su come ottenere un elenco di frammenti di codice installati per il servizio di linguaggio, vedere [Procedura dettagliata: Ottenere un elenco di frammenti di codice installato \(implementazione Legacy\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).  
  
## Implementazione della classe ExpansionFunction  
 Una funzione di espansione è una funzione denominata che è incorporata in un modello di frammento e restituisce uno o più valori da inserire in un campo. Per supportare le funzioni di espansione nel servizio di linguaggio, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe e implementare il <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metodo. È quindi necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> metodo nel <xref:Microsoft.VisualStudio.Package.LanguageService> classe per restituire una nuova istanza della versione della <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe per ogni funzione di espansione è supportata. Se si supporta un elenco di possibili valori da una funzione di espansione, è necessario inoltre eseguire l'override di <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> metodo la <xref:Microsoft.VisualStudio.Package.ExpansionFunction> classe per restituire un elenco di tali valori.  
  
 Una funzione di espansione che accetta argomenti o richiede l'accesso a altri campi non deve essere associata a un campo modificabile, come il provider di espansione potrebbe non essere inizializzato completamente nel momento in cui che viene chiamata la funzione di espansione. Di conseguenza, la funzione di espansione non è in grado di ottenere il valore dei relativi argomenti o qualsiasi altro campo.  
  
### Esempio  
 Di seguito è riportato un esempio di come chiama una funzione semplice espansione `GetName` potrebbe essere implementato. Questa funzione di espansione viene aggiunto un numero al nome di una classe base ogni volta che viene creata un'istanza la funzione di espansione \(che corrisponde a ogni volta che il frammento di codice associato viene inserito\).  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Frammenti di codice](../../ide/code-snippets.md)   
 [Procedura dettagliata: Ottenere un elenco di frammenti di codice installato \(implementazione Legacy\)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)