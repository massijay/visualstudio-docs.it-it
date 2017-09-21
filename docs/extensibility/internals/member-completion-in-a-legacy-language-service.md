---
title: "Completamento di membro in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense, descrizione membro completamento"
  - "Completamento del membro supporto in servizi di linguaggio [framework pacchetto gestito]"
  - "servizi di linguaggio [framework gestito pacchetto], completamento IntelliSense membro"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Completamento di membro in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il completamento di membri IntelliSense è una descrizione comandi che visualizza un elenco di possibili membri di un ambito specifico, ad esempio una classe, struttura, enumerazione o dello spazio dei nomi. Ad esempio, in c\#, se l'utente digita "this" seguito da un punto, un elenco di tutti i membri della classe o struttura nell'ambito corrente è presentato in un elenco da cui l'utente può selezionare.  
  
 Il framework di pacchetto gestito \(MPF\) fornisce supporto per la descrizione comando e la gestione dell'elenco nella descrizione comando; è sufficiente è cooperazione dal parser per fornire i dati visualizzati nell'elenco.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Come funziona  
 Di seguito sono due modi in cui viene visualizzato un elenco di membri utilizzando le classi MPF:  
  
-   Posizionare il punto di inserimento su un identificatore o dopo un carattere di completamento del membro e selezionando **Elenca membri** dal **IntelliSense** menu.  
  
-   Il <xref:Microsoft.VisualStudio.Package.IScanner> scanner rileva un carattere di completamento del membro e imposta un trigger di token <xref:Microsoft.VisualStudio.Package.TokenTriggers> per tale carattere.  
  
 Un carattere di completamento membro indica che un membro di una classe, struttura o enumerazione consiste nel seguire. In c\# o Visual Basic, ad esempio, il carattere di completamento membro è un `.`, mentre in C\+\+ il carattere è un `.` o `->`. Il valore trigger viene impostato durante l'analisi di carattere selezionare il membro.  
  
### Il comando di elenco di membri in IntelliSense  
 Il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo la <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> \(metodo\), a sua volta, chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Il parser determina il contesto della posizione corrente, nonché il token in o immediatamente prima della posizione corrente. In base a questo token, viene presentato un elenco di dichiarazioni. Ad esempio, in c\#, se si posiziona il cursore su un membro di classe e selezionare **Elenca membri**, si ottiene un elenco di tutti i membri della classe. Se si posiziona il cursore dopo un periodo che segue una variabile oggetto, ottenere un elenco di tutti i membri della classe di tale oggetto rappresenta. Si noti che se il punto di inserimento viene posizionato su un membro quando viene visualizzato l'elenco dei membri, selezionare un membro dall'elenco sostituisce il membro che è attivo il cursore con uno nell'elenco.  
  
### Il Trigger di Token  
 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> trigger avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo il <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo chiama a sua volta, il parser con il motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> \(se il trigger di token è inoltre incluso il <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag, il motivo per l'analisi è <xref:Microsoft.VisualStudio.Package.ParseReason> che combina selezione dei membri e l'evidenziazione delle parentesi graffe\).  
  
 Il parser determina il contesto dell'oggetto corrente della posizione nonché digitato prima che il membro selezionare carattere. Da queste informazioni, il parser crea un elenco di tutti i membri dell'ambito richiesto. Incluso in questo elenco di dichiarazioni di <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(metodo\). Se vengono restituite tutte le dichiarazioni, viene visualizzata la descrizione comando completamento membro. La descrizione comandi sono gestito da un'istanza di <xref:Microsoft.VisualStudio.Package.CompletionSet> \(classe\).  
  
## Abilita il supporto per il completamento di membro  
 È necessario disporre di `CodeSense` voce del Registro di sistema è impostato su 1 per supportare qualsiasi operazione di IntelliSense. Questa voce del Registro di sistema può essere impostata con un parametro denominato passato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Le classi del servizio di linguaggio leggono il valore di questa voce del Registro di sistema dalla <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Se lo scanner restituisce il token trigger di <xref:Microsoft.VisualStudio.Package.TokenTriggers>, il parser restituisce un elenco di dichiarazioni, quindi viene visualizzato l'elenco di completamento del membro.  
  
## Supporto completamento membro nello Scanner  
 Lo scanner deve essere in grado di rilevare un carattere di completamento del membro e impostare il trigger di token <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando tale carattere viene analizzato.  
  
### Esempio  
 Ecco un esempio semplificato di rilevare il carattere di completamento del membro e l'impostazione appropriata <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo. Nell'esempio di codice imposta semplicemente il trigger quando viene rilevato il tipo di carattere corretto.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## Supporto di membro completamento nel Parser  
 Per il completamento di membro, la <xref:Microsoft.VisualStudio.Package.Source> classe chiamate di <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo. È necessario implementare l'elenco in una classe che deriva dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe. Vedere la <xref:Microsoft.VisualStudio.Package.Declarations> classe per informazioni dettagliate sui metodi di cui è necessario implementare.  
  
 Il parser viene chiamato con <xref:Microsoft.VisualStudio.Package.ParseReason> o <xref:Microsoft.VisualStudio.Package.ParseReason> quando viene digitato un carattere di selezione del membro. Il percorso specificato <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto si trova immediatamente dopo il membro selezionato carattere. Il parser deve raccogliere i nomi di tutti i membri che possono essere visualizzati in un elenco di membri in tale particolare punto nel codice sorgente. Quindi il parser deve analizzare la riga corrente per determinare l'ambito che il consenso dell'utente associato al carattere selezionare membro.  
  
 Questo ambito è in base al tipo dell'identificatore prima che il membro selezionare carattere. In c\#, si consideri ad esempio la variabile membro `languageService` che dispone di un tipo di `LanguageService`, digitando **languageService.** produce un elenco di tutti i membri della `LanguageService` classe. Anche in c\#, digitare **questo.** produce un elenco di tutti i membri della classe nell'ambito corrente.  
  
### Esempio  
 Nell'esempio seguente viene illustrato come popolare un <xref:Microsoft.VisualStudio.Package.Declarations> elenco. Questo codice presuppone che il parser crea una dichiarazione e lo aggiunge all'elenco chiamando un `AddDeclaration` metodo la `TestAuthoringScope` classe.  
  
```c#  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```