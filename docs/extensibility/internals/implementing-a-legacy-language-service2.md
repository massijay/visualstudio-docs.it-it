---
title: "Implementazione di un Service2 Language Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio [framework gestito pacchetto], implementazione"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Implementazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Per implementare un servizio di linguaggio utilizzando il framework \(MPF\) gestito del pacchetto, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.LanguageService> e implementare i seguenti metodi e proprietà astratti:  
  
-   Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   Metodo <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   Proprietà <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
 Vedere le sezioni appropriate di seguito per informazioni dettagliate sull'implementazione di tali metodi e proprietà.  
  
 Per supportare le funzionalità aggiuntive, il servizio di linguaggio essere necessario derivare una classe da una delle classi del servizio di linguaggio di MPF; ad esempio, per supportare i comandi di menu aggiuntive, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.ViewFilter> ed eseguire l'override di molti metodi di gestione del comando \(vedere <xref:Microsoft.VisualStudio.Package.ViewFilter> per i dettagli\).  La classe di <xref:Microsoft.VisualStudio.Package.LanguageService> fornisce una serie di metodi chiamati per creare nuove istanze delle classi e si esegue l'override del metodo appropriato di creazione per fornire un'istanza della classe.  Ad esempio, è necessario eseguire l'override del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> per restituire un'istanza della classe per contenere la classe di <xref:Microsoft.VisualStudio.Package.ViewFilter> .  Vedere “creazione di istanze delle classi personalizzate„ per la sezione per ulteriori informazioni.  
  
 Il servizio di linguaggio possono anche fornire le proprie icone, utilizzate in più posizioni.  Ad esempio, quando un elenco di completamento IntelliSense viene visualizzato, ogni elemento nell'elenco può contenere un'icona associata a, contrassegnando l'elemento come metodo, classe, lo spazio dei nomi, proprietà, o qualsiasi necessaria per il linguaggio.  Queste icone vengono utilizzate in tutti gli elenchi di IntelliSense, **barra di navigazione**e nella finestra di attività di **Elenco errori** .  Vedere la sezione “immagini del servizio di linguaggio„ riportata di seguito per i dettagli.  
  
## metodo di GetLanguagePreferences  
 il metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> restituisce sempre la stessa istanza di una classe di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  È possibile utilizzare la classe base di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> se non è necessaria alcuna preferenze aggiuntive per il servizio di linguaggio.  Le classi del servizio di linguaggio di MPF si presuppone la presenza di almeno della classe base di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
### Esempio  
 In questo esempio viene illustrata un'implementazione tipica del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> .  In questo esempio la classe base di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(TestLanguageService).GUID,  
                                                        this.Name );  
                m_preferences.Init();  
            }  
            return m_preferences;  
        }  
    }  
}  
```  
  
## metodo di GetScanner  
 Questo metodo restituisce un'istanza di un oggetto di <xref:Microsoft.VisualStudio.Package.IScanner> che implementa un parser o uno scanner riga orientata utilizzato per ottenere i token e i tipi e trigger.  Questo analisi viene utilizzato nella classe di <xref:Microsoft.VisualStudio.Package.Colorizer> per colorazione sebbene lo scanner possa essere utilizzato per ottenere i tipi e i trigger simbolici come preludio in un'operazione di analisi più complessa.  È necessario garantire la classe che implementa l'interfaccia di <xref:Microsoft.VisualStudio.Package.IScanner> ed è necessario implementare tutti i metodi sull'interfaccia di <xref:Microsoft.VisualStudio.Package.IScanner> .  
  
### Esempio  
 In questo esempio viene illustrata un'implementazione tipica del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> .  La classe di `TestScanner` implementa l'interfaccia di <xref:Microsoft.VisualStudio.Package.IScanner> \(non visualizzata\).  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private TestScanner m_scanner;  
  
        public override IScanner GetScanner(IVsTextLines buffer)  
        {  
            if (m_scanner == null)  
            {  
                m_scanner = new TestScanner(buffer);  
            }  
            return m_scanner;  
        }  
    }  
}  
    internal class TestScanner : IScanner  
    {  
        private IVsTextBuffer m_buffer;  
        string m_source;  
  
        public TestScanner(IVsTextBuffer buffer)  
        {  
            m_buffer = buffer;  
        }  
  
        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)  
        {  
            tokenInfo.Type = TokenType.Unknown;  
            tokenInfo.Color = TokenColor.Text;  
            return true;  
        }  
  
        void IScanner.SetSource(string source, int offset)  
        {  
            m_source = source.Substring(offset);  
        }  
    }  
  
```  
  
## metodo di ParseSource  
 Analizza il file di origine basato su alcune situazioni diverse.  Questo metodo viene fornito un oggetto di <xref:Microsoft.VisualStudio.Package.ParseRequest> che indichi cosa è previsto da un'operazione di analisi specifico.  Il metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> richiama un parser più complesso che determina la funzionalità e l'ambito token.  Il metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> viene utilizzato per attivare le operazioni nonché la corrispondenza di parentesi graffe di IntelliSense.  Anche se non supportate tali operazioni avanzate, è necessario restituire un oggetto valido di <xref:Microsoft.VisualStudio.Package.AuthoringScope> e che è necessario creare una classe che implementa l'interfaccia di <xref:Microsoft.VisualStudio.Package.AuthoringScope> e implementa tutti i metodi in tale interfaccia.  È possibile restituire valori null da tutti i metodi mentre l'oggetto stesso di <xref:Microsoft.VisualStudio.Package.AuthoringScope> non deve essere un valore null.  
  
### Esempio  
 In questo esempio viene illustrata un'implementazione minima del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> e della classe di <xref:Microsoft.VisualStudio.Package.AuthoringScope> , sufficiente per consentire al servizio di linguaggio venga compilato ed eseguito senza doverli effettivamente supportare qualsiasi delle funzionalità più avanzate.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            return new TestAuthoringScope();  
        }  
    }  
  
    internal class TestAuthoringScope : AuthoringScope  
    {  
        public override string GetDataTipText(int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return null;  
        }  
  
        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)  
        {  
            span = new TextSpan();  
            return null;  
        }  
  
        public override Methods GetMethods(int line, int col, string name)  
        {  
            return null;  
        }  
}  
```  
  
## Proprietà name  
 Questa proprietà restituisce il nome del servizio di linguaggio.  Questa operazione deve essere lo stesso nome fornito quando il servizio di linguaggio è stato registrato.  Questo nome viene utilizzato in una serie di punti, il più rilevante dei quali è la classe di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> in cui il nome verrà utilizzato per accedere al Registro di sistema.  Il nome restituito dalla proprietà non deve essere localizzato mentre è utilizzato nel Registro di sistema per la voce del Registro di sistema e i nomi delle chiavi.  
  
### Esempio  
 In questo esempio viene illustrata un'implementazione possibile della proprietà di <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> .  Si noti che il nome è specificato: il nome effettivo deve essere ottenuto da un file di risorse in modo che possa essere utilizzato in registrare un servizio di linguaggio \(vedere [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override string Name  
        {  
            get { return "Test Language"; }  
        }  
    }  
}  
```  
  
## Creazione di istanze delle classi personalizzate  
 The following methods in the specified classes can be overridden to provide instances of your own versions of each class.  
  
### Nella classe di LanguageService  
  
|Metodo|classe restituita|Descrizione|  
|------------|-----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Per supportare le aggiunte personalizzate alla visualizzazione di testo.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Per supportare le proprietà personalizzate del documento.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Per supportare **barra di navigazione**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Per supportare le funzioni nei modelli del frammento di codice.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Per supportare i frammenti di codice \(questo metodo non viene in genere eseguito l'override\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Per supportare la personalizzazione della struttura di <xref:Microsoft.VisualStudio.Package.ParseRequest> \(questo metodo non viene in genere eseguito l'override\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Per supportare codice sorgente di formattazione, specificando i caratteri di commenti e personalizzante le firme del metodo.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Per supportare i comandi di menu aggiuntivi.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Per supportare evidenziazione della sintassi \(questo metodo non viene in genere eseguito l'override\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Per supportare accesso alle preferenze di lingua.  Questo metodo deve essere implementato ma può restituire un'istanza della classe base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Per fornire un parser utilizzato per l'identificazione dei tipi di token in una riga.  Questo metodo deve essere distribuito e <xref:Microsoft.VisualStudio.Package.IScanner> deve essere derivato da.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Per fornire un parser utilizzato per l'identificazione funzionalità e dell'ambito di un intero file di origine.  Questo metodo deve essere distribuito e deve restituire un'istanza della versione della classe di <xref:Microsoft.VisualStudio.Package.AuthoringScope> .  Se tutto ciò che si desidera supportare alcuna evidenziazione della sintassi \(che richiede il parser di <xref:Microsoft.VisualStudio.Package.IScanner> restituito dal metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> \), è possibile non eseguire alcuna operazione in questo metodo diverso da restituire una versione di metodi della classe di <xref:Microsoft.VisualStudio.Package.AuthoringScope> di cui tutti i valori null di restituire.|  
  
### Nella classe di origine  
  
|Metodo|classe restituita|Descrizione|  
|------------|-----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Per personalizzare la visualizzazione degli elenchi di completamento IntelliSense \(questo metodo non viene in genere eseguito l'override\).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Per i marcatori di supporto l'elenco delle attività di Elenco errori; in particolare, supporto per le funzionalità oltre aprire il file e passare alla riga che ha provocato l'errore.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Per personalizzare la visualizzazione delle descrizioni comandi di informazioni parametri di IntelliSense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Per il codice di commento di supporto.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Per raccogliere informazioni durante l'operazione di analisi.|  
  
### Nella classe di AuthoringScope  
  
|Metodo|classe restituita|Descrizione|  
|------------|-----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Viene fornito un elenco delle dichiarazioni dei membri o tipi.  Questo metodo deve essere implementato ma può restituire un valore null.  Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione della classe di <xref:Microsoft.VisualStudio.Package.Declarations> .|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Viene fornito un elenco delle firme del metodo per un determinato contesto.  Questo metodo deve essere implementato ma può restituire un valore null.  Se questo metodo restituisce un oggetto valido, l'oggetto deve essere un'istanza della versione della classe di <xref:Microsoft.VisualStudio.Package.Methods> .|  
  
## Immagini del servizio di linguaggio  
 Per fornire un elenco di icone da utilizzare in qualsiasi servizio di linguaggio, eseguire l'override del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> e restituire <xref:System.Windows.Forms.ImageList> che contiene icone.  I caricamenti di classe base di <xref:Microsoft.VisualStudio.Package.LanguageService> una serie di icone.  Poiché si specifica l'indice esatto di immagini nei casi che necessitano delle icone, ad esempio si dispone dell'elenco di immagini dipende interamente il programmatore.  
  
### Immagini utilizzate negli elenchi di completamento IntelliSense  
 Per gli elenchi di completamento IntelliSense, l'indice immagine è specificato per ogni elemento nel metodo di <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> della classe di <xref:Microsoft.VisualStudio.Package.Declarations> , che è necessario eseguire l'override se si desidera fornire un indice di immagine.  Il valore restituito dal metodo di <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> è un indice nell'elenco immagini fornito al costruttore della classe di <xref:Microsoft.VisualStudio.Package.CompletionSet> e che è lo stesso elenco immagini restituito dal metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> \(è possibile cambiare che elenco immagini da utilizzare per <xref:Microsoft.VisualStudio.Package.CompletionSet> se si esegue l'override del metodo di <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> nella classe di <xref:Microsoft.VisualStudio.Package.Source> per fornire un elenco immagini diverso\).  
  
### Immagini utilizzate nella barra di navigazione  
 **barra di navigazione** visualizzare gli elenchi di tipi e membri e viene utilizzato per la navigazione rapida possibile visualizzare le icone.  Queste icone vengono ottenute dal metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> e non è possibile eseguire l'override in modo specifico per **barra di navigazione**.  Gli indici utilizzati per ogni elemento nelle caselle combinate vengono specificati quando gli elenchi che rappresentano le caselle combinate vengono sostituiti con il metodo di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> nella classe di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> \(vedere [Supporto per la barra di spostamento in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\).  Questi indici di immagine vengono ottenuti in qualche modo dal parser, in genere tramite la versione della classe di <xref:Microsoft.VisualStudio.Package.Declarations> .  Come gli indici vengono ottenuti dipende interamente il programmatore.  
  
### Immagini utilizzate nella finestra di attività di Elenco errori  
 Ogni volta che il parser del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(vedere [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)\) rileva un errore e la passa all'errore al metodo di <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> nella classe di <xref:Microsoft.VisualStudio.Package.AuthoringSink> , viene segnalato l'errore nella finestra di attività di **Elenco errori** .  Un'icona può essere associata a ogni elemento visualizzato nella finestra di attività e che l'icona dallo stesso elenco immagini restituito dal metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> .  Il comportamento predefinito delle classi di MPF consiste nel non visualizzare un'immagine con il messaggio di errore.  Tuttavia, è possibile eseguire l'override di questo comportamento derivando una classe dalla classe di <xref:Microsoft.VisualStudio.Package.Source> ed eseguendo l'override del metodo di <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> .  In questo metodo, viene creato un nuovo oggetto di <xref:Microsoft.VisualStudio.Package.DocumentTask> .  Prima di restituire tale oggetto, è possibile utilizzare la proprietà di <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> l'oggetto di <xref:Microsoft.VisualStudio.Package.DocumentTask> per impostare il valore dell'immagine.  Ciò è analogo al seguente esempio.  Si noti che `TestIconImageIndex` è un'enumerazione che elenca le icone ed è specifico di questo esempio.  È possibile avere un modo diverso di identificazione delle icone nel servizio di linguaggio.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestSource : Source  
    {  
        public override DocumentTask CreateErrorTaskItem(  
            TextSpan          span,  
            string            filename,  
            string            message,  
            TastPriority      priority,  
            TaskCategory      category,  
            MARKERTYPE        markerType,  
            TaskErrorCategory errorCategory)  
        {  
            DocumentTask taskItem = base.CreateErrorTaskItem(  
                                           span,  
                                           filename,  
                                           message,  
                                           priority,  
                                           category,  
                                           markerType,  
                                           errorCategory);  
            if (errorCategory == TaskErrorCategory.Error)  
            {  
                taskItem.ImageIndex = TestIconImageIndex.Error;  
            }  
            return taskItem;  
        }  
    }  
}  
```  
  
## l'elenco di immagini predefinito per un servizio di linguaggio  
 L'elenco di immagini predefinito fornito con le classi del servizio di linguaggio di base MPF contiene una serie di icone associate agli elementi del linguaggio più comuni.  La maggior parte di queste icone viene disposto in set di sei variazioni, corrispondente ai concetti di accesso pubblico, interni, friend, di protetto, di privato e collegamento.  Ad esempio, è possibile includere icone diverse per un metodo come se è pubblico, protetto o privato.  
  
 Nell'enumerazione specifica i nomi comuni per ogni set di icone e specifica l'indice associato.  Ad esempio, in base all'enumerazione, è possibile specificare l'indice di immagini per un metodo protetto come `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`.  È possibile modificare queste caratteristiche specificando i flag quando si definisce la barra degli strumenti nel file .vsct, come illustrato nella procedura riportata di seguito.  
  
```c#  
public enum IconImageIndex  
        {  
            // access types  
            AccessPublic = 0,  
            AccessInternal = 1,  
            AccessFriend = 2,  
            AccessProtected = 3,  
            AccessPrivate = 4,  
            AccessShortcut = 5,  
  
            Base = 6,  
            // Each of the following icon type has 6 versions,  
            //corresponding to the access types  
            Class = Base + 0,  
            Constant = Base + 1,  
            Delegate = Base + 2,  
            Enumeration = Base + 3,  
            EnumMember = Base + 4,  
            Event = Base + 5,  
            Exception = Base + 6,  
            Field = Base + 7,  
            Interface = Base + 8,  
            Macro = Base + 9,  
            Map = Base + 10,  
            MapItem = Base + 11,  
            Method = Base + 12,  
            OverloadedMethod = Base + 13,  
            Module = Base + 14,  
            Namespace = Base + 15,  
            Operator = Base + 16,  
            Property = Base + 17,  
            Struct = Base + 18,  
            Template = Base + 19,  
            Typedef = Base + 20,  
            Type = Base + 21,  
            Union = Base + 22,  
            Variable = Base + 23,  
            ValueType = Base + 24,  
            Intrinsic = Base + 25,  
            JavaMethod = Base + 26,  
            JavaField = Base + 27,  
            JavaClass = Base + 28,  
            JavaNamespace = Base + 29,  
            JavaInterface = Base + 30,  
            // Miscellaneous icons with one icon for each type.  
            Error = 187,  
            GreyedClass = 188,  
            GreyedPrivateMethod = 189,  
            GreyedProtectedMethod = 190,  
            GreyedPublicMethod = 191,  
            BrowseResourceFile = 192,  
            Reference = 193,  
            Library = 194,  
            VBProject = 195,  
            VBWebProject = 196,  
            CSProject = 197,  
            CSWebProject = 198,  
            VB6Project = 199,  
            CPlusProject = 200,  
            Form = 201,  
            OpenFolder = 202,  
            ClosedFolder = 203,  
            Arrow = 204,  
            CSClass = 205,  
            Snippet = 206,  
            Keyword = 207,  
            Info = 208,  
            CallBrowserCall = 209,  
            CallBrowserCallRecursive = 210,  
            XMLEditor = 211,  
            VJProject = 212,  
            VJClass = 213,  
            ForwardedType = 214,  
            CallsTo = 215,  
            CallsFrom = 216,  
            Warning = 217,  
        }  
```  
  
## Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Cenni preliminari sul servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-overview.md)   
 [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)