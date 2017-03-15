---
title: Colorazione della sintassi in un servizio di linguaggio Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b9d98323b3957108746b22702306c9155b142fb9
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio Legacy
Colorazione della sintassi è una funzionalità che determina i diversi elementi di un linguaggio di programmazione da visualizzare in un file di origine in diversi colori e stili. Per supportare questa funzionalità, è necessario fornire un parser o un programma in grado di identificare i tipi di elementi lessicali o token nel file. Molti linguaggi di distinguono le parole chiave, i delimitatori (ad esempio le parentesi o parentesi graffe) e i commenti da essi colorare in modi diversi.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation"></a>Implementazione  
 Per supportare la colorazione, il framework di pacchetto gestito (MPF) comprende la <xref:Microsoft.VisualStudio.Package.Colorizer>classe che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>interfaccia.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.Package.Colorizer> Questa classe interagisce con un <xref:Microsoft.VisualStudio.Package.IScanner>per determinare i token e i colori.</xref:Microsoft.VisualStudio.Package.IScanner> Per ulteriori informazioni su scanner, vedere [Scanner e Parser servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer>classe quindi contrassegna ogni carattere del token con le informazioni sui colori e restituisce le informazioni all'editor la visualizzazione del file di origine.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 Le informazioni sui colori restituiti per l'editor è un indice in un elenco di colori. Ogni elemento colorabile specifica un valore di colore e un set di attributi di tipo di carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi di colore predefiniti che è possibile utilizzare il servizio di linguaggio. È necessario eseguire è specificare l'indice di colore appropriato per ogni tipo di token. Tuttavia, è possibile fornire un set di elementi di colori personalizzati e gli indici che è fornire per i token e fare riferimento a un elenco di elementi colorabili invece dell'elenco predefinito. È inoltre necessario impostare il `RequestStockColors` voce del Registro di sistema su 0 (o non si specifica il `RequestStockColors` voce affatto) per supportare colori personalizzati. È possibile impostare questa voce del Registro di sistema con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>attributo definito dall'utente.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Per ulteriori informazioni sulla registrazione di un servizio di linguaggio e impostando le relative opzioni, vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Elementi di colori personalizzati  
 Per fornire i propri elementi di colori personalizzati, è necessario eseguire l'override <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>e il <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> Il primo metodo restituisce il numero di elementi di colori personalizzati che supporta il servizio di linguaggio e il secondo Ottiene l'elemento colorabile predefinito in base all'indice. Creare l'elenco predefinito di elementi di colori personalizzati. Nel costruttore del servizio di linguaggio, è sufficiente eseguire è specificare ogni elemento colorabile predefinito con un nome. Visual Studio gestisce automaticamente nel caso in cui l'utente seleziona un diverso set di colori. Questo nome viene visualizzato un messaggio nel **tipi di carattere e colori** pagina proprietà di **opzioni** la finestra di dialogo (disponibile da Visual Studio **strumenti** menu) e tale nome determina il colore di un utente ha eseguito l'override. Le scelte dell'utente sono archiviate in una cache nel Registro di sistema e accessibili dal nome del colore. Il **tipi di carattere e colori** pagina delle proprietà sono elencati tutti i nomi dei colori in ordine alfabetico, pertanto è possibile raggruppare i colori personalizzati facendo precedere ogni nome di colore con il nome della lingua; ad esempio, "**TestLanguage - commento**"e"**TestLanguage - parola chiave**". Oppure è possibile raggruppare gli elementi colorabile predefiniti dal tipo, "**commento (TestLanguage)**"e"**(parola chiave) (TestLanguage)**". Raggruppamento in base al nome di lingua è preferito.  
  
> [!CAUTION]
>  Si consiglia di includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi di elemento colorabile esistenti.  
  
> [!NOTE]
>  Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario azzerare la cache creati in Visual Studio al primo accesso i colori sono stati. È possibile farlo eseguendo il **reimpostare l'Hive sperimentale** comando dal menu di programma di Visual Studio SDK.  
  
 Si noti che il primo elemento nell'elenco di colori non viene mai fatto riferimento. Visual Studio fornisce sempre i colori predefiniti del testo e gli attributi per tale elemento. Il modo più semplice di gestire questa è di fornire un elemento colorabile segnaposto come primo elemento.  
  
### <a name="high-color-colorable-items"></a>Elementi colorabile High Color  
 Colori possono supportare anche valori di colore a 24 bit o ad alta tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interfaccia.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> Il MPF <xref:Microsoft.VisualStudio.Package.ColorableItem>classe supporta il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>interfaccia e i colori a 24 bit vengono specificati nel costruttore con i colori normale.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.Package.ColorableItem> Vedere la <xref:Microsoft.VisualStudio.Package.ColorableItem>classe per altri dettagli.</xref:Microsoft.VisualStudio.Package.ColorableItem> Nell'esempio seguente viene illustrato come impostare i colori a 24 bit per le parole chiave e commenti. I colori a 24 bit vengono utilizzati quando colore a 24 bit è supportato sul desktop dell'utente; in caso contrario, vengono utilizzati i colori di testo normale.  
  
 Tenere presente che questi sono i colori predefiniti per il linguaggio. l'utente può modificare i colori come desiderano.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrato come dichiarare e popola una matrice di elementi di colori personalizzati utilizzando la <xref:Microsoft.VisualStudio.Package.ColorableItem>classe.</xref:Microsoft.VisualStudio.Package.ColorableItem> In questo esempio i colori di parola chiave e il commento con colori a 24 bit.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>La classe di rappresentazione e Scanner  
 La base <xref:Microsoft.VisualStudio.Package.LanguageService>classe dispone di un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>metodo tale <xref:Microsoft.VisualStudio.Package.Colorizer>classe.</xref:Microsoft.VisualStudio.Package.Colorizer> instantiantes</xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Lo scanner restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>viene passato per il <xref:Microsoft.VisualStudio.Package.Colorizer>costruttore della classe.</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
 È necessario implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>metodo in una versione personalizzata della <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> La <xref:Microsoft.VisualStudio.Package.Colorizer>classe utilizza il programma antivirus per ottenere tutte le informazioni colore token.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 È necessario lo scanner popolare un <xref:Microsoft.VisualStudio.Package.TokenInfo>struttura per ogni token si trova.</xref:Microsoft.VisualStudio.Package.TokenInfo> Questa struttura contiene informazioni quali occupa l'intervallo di token, l'indice di colore da utilizzare, il tipo è il token e token di trigger (vedere <xref:Microsoft.VisualStudio.Package.TokenTriggers>).</xref:Microsoft.VisualStudio.Package.TokenTriggers> Sono necessari solo l'indice di intervallo e il colore per colorazione dalla <xref:Microsoft.VisualStudio.Package.Colorizer>classe.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 L'indice di colore archiviato nel <xref:Microsoft.VisualStudio.Package.TokenInfo>struttura è in genere un valore compreso il <xref:Microsoft.VisualStudio.Package.TokenColor>enumerazione che fornisce una serie di indici denominati corrispondente a vari elementi del linguaggio, ad esempio operatori e parole chiave.</xref:Microsoft.VisualStudio.Package.TokenColor> </xref:Microsoft.VisualStudio.Package.TokenInfo> Se gli elementi di colori personalizzati Elenca risultati gli elementi presentato nel <xref:Microsoft.VisualStudio.Package.TokenColor>enumerazione, quindi si può semplicemente utilizzare l'enumerazione come colore per ogni token.</xref:Microsoft.VisualStudio.Package.TokenColor> Tuttavia, se si dispone di ulteriori elementi colorabili o non si desidera utilizzare i valori esistenti in tale ordine, è possibile ordinare l'elenco di elementi di colori personalizzati per le esigenze e restituire l'indice appropriato nell'elenco. Assicurarsi di eseguire il cast dell'indice per un <xref:Microsoft.VisualStudio.Package.TokenColor>Quando archiviare i dati nella struttura <xref:Microsoft.VisualStudio.Package.TokenInfo>; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] Visualizza solo l'indice.</xref:Microsoft.VisualStudio.Package.TokenInfo> </xref:Microsoft.VisualStudio.Package.TokenColor>  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come lo scanner potrebbe identificare tre tipi di token: identificatori (tutto ciò che non è un numero o segni di punteggiatura), segni di punteggiatura e numeri. Questo esempio è solo a scopo illustrativo e non rappresenta un'implementazione completa dello scanner e parser. Si presuppone che esista un `Lexer` classe con un `GetNextToken()` metodo che restituisce una stringa.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
