---
title: "Corrispondenza di parentesi in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "corrispondenza parentesi graffe"
  - "servizi di linguaggio [framework gestito pacchetto], corrispondenza parentesi graffe"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Corrispondenza di parentesi in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Corrispondenza parentesi graffe consente allo sviluppatore di tenere traccia di elementi del linguaggio che si verificano insieme, ad esempio le parentesi e parentesi graffe è necessario. Quando uno sviluppatore inserisce una parentesi graffa di chiusura, parentesi graffa di apertura viene evidenziata.  
  
 È possibile confrontare due o tre elementi che si verificano contemporaneamente, denominati coppie e Triple. Triple sono set di tre elementi che si verificano contemporaneamente. Ad esempio, in c\#, il `foreach` istruzione costituisce una tripla: "`foreach()`","`{`", e "`}`". Tutti e tre gli elementi vengono evidenziati quando viene digitata la parentesi graffa di chiusura.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare corrispondenza parentesi graffe, vedere [Procedura dettagliata: Visualizzazione di parentesi graffe corrispondenti](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 La <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe supporta entrambe le coppie e per triplica con il <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> e <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metodi.  
  
## Implementazione  
 Il servizio di linguaggio deve identificare tutti gli elementi corrispondenti nel linguaggio e quindi individuare tutte le coppie corrispondenti. Questa operazione viene in genere eseguita implementando <xref:Microsoft.VisualStudio.Package.IScanner> per rilevare una lingua corrispondente e viene quindi utilizzato il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo corrispondenti agli elementi.  
  
 Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo chiama il programma antivirus per suddividere la riga e restituire il token che precede il cursore. Lo scanner indica che è stata trovata una coppia di elementi di linguaggio impostando il valore trigger token <xref:Microsoft.VisualStudio.Package.TokenTriggers> sul token corrente. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> chiamate al metodo di <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodo che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metodo con il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> per individuare l'elemento di linguaggio corrispondente. Quando viene trovato l'elemento di linguaggio corrispondente, entrambi gli elementi vengono evidenziati.  
  
 Per una descrizione completa di come digitando una parentesi graffa attiva l'evidenziazione delle parentesi graffe, vedere la sezione "Operazione di analisi di esempio" nell'argomento [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## Abilita il supporto per la corrispondenza delle parentesi graffe  
 Il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> impostare l'attributo di `MatchBraces`, `MatchBracesAtCaret`, e `ShowMatchingBrace` parametri denominati che imposteranno le proprietà corrispondenti della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Proprietà preferenza lingua possono anche essere impostate dall'utente.  
  
|Voce del Registro di sistema|Proprietà|Descrizione|  
|----------------------------------|---------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Corrispondenza parentesi graffe consente|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Abilita corrispondenza parentesi graffe come punto di inserimento viene spostato.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Evidenzia la parentesi graffa corrispondente.|  
  
## Corrispondenza di istruzioni condizionali  
 È possibile far corrispondere le istruzioni condizionali, ad esempio `if`, `else if`, e `else`, o `#if`, `#elif`, `#else`, `#endif`, nello stesso modo come delimitatori di corrispondenza. È possibile creare una sottoclasse di <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe e forniscono un metodo che è possibile aggiungere testo si estende oltre i delimitatori per la matrice interna di elementi corrispondenti.  
  
## Impostazione di Trigger  
 Nell'esempio seguente viene illustrato come rilevare la corrispondenza tra parentesi, parentesi graffe e parentesi quadre e impostare il trigger per tale nello scanner. Il <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> metodo la <xref:Microsoft.VisualStudio.Package.Source> classe rileva il trigger e chiama il parser per trovare la coppia corrispondente \(vedere la sezione "Individuazione Match" in questo argomento\). Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## Corrispondenza parentesi graffe  
 Ecco un esempio semplificato per far corrispondere il {} elementi di linguaggio, \(\) e \[\] e i relativi intervalli per l'aggiunta di <xref:Microsoft.VisualStudio.Package.AuthoringSink> oggetto. Questo approccio non è un approccio consigliato per l'analisi del codice sorgente; è solo a scopo illustrativo.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)