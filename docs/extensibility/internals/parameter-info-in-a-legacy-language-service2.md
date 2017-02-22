---
title: "Informazioni sui parametri in un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "IntelliSense, descrizione comandi per informazioni di parametro"
  - "servizi di linguaggio [framework gestito pacchetto], informazioni sul parametro di IntelliSense"
  - "Informazioni parametri (IntelliSense), supporto in servizi di linguaggio [framework pacchetto gestito]"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Informazioni sui parametri in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Informazioni sul parametro IntelliSense è una descrizione comando che consente di visualizzare la firma di un metodo quando l'utente digita l'elenco dei parametri start carattere \(in genere una parentesi di apertura\) per l'elenco di parametri di metodo. Quando viene immesso ogni parametro e il separatore di parametro \(in genere una virgola\) è tipizzato, la descrizione comando viene aggiornata per mostrare il parametro successivo in grassetto.  
  
 Le classi di framework \(MPF\) pacchetto gestito forniscono il supporto per la gestione della descrizione comando informazioni sul parametro. Il parser deve rilevare parametro start parametro successivo, e caratteri di fine dei parametri e deve fornire un elenco di firme del metodo e i relativi parametri.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Implementazione  
 Il parser deve impostare il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> viene impostata quando rileva un carattere di inizio elenco parametro \(spesso una parentesi aperta\). Deve essere impostato un <xref:Microsoft.VisualStudio.Package.TokenTriggers> attivare quando rileva un separatore di parametri \(spesso una virgola\). In questo modo una descrizione comando informazioni sul parametro devono essere aggiornati e visualizzare il parametro successivo in grassetto. Il parser deve impostare il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando se rileva il carattere di fine elenco parametro \(spesso una parentesi chiusa\).  
  
 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> valore trigger avvia una chiamata per il <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metodo, che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con un motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Se il parser rileva che l'identificatore l'elenco dei parametri prima di carattere è un nome di metodo riconosciuto, viene restituito un elenco di firme del metodo in corrispondenza di <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Se sono state trovate le firme di metodo e la descrizione comando informazioni sul parametro viene visualizzata con la firma prima nell'elenco. Questa descrizione comandi viene quindi aggiornata di più della firma. Quando si digita il carattere di fine elenco di parametri, la descrizione comando informazioni sul parametro viene rimosso dalla visualizzazione.  
  
> [!NOTE]
>  Per garantire che la descrizione comando informazioni sul parametro sia formattata correttamente, è necessario eseguire l'override di proprietà nella <xref:Microsoft.VisualStudio.Package.Methods> classe per fornire i caratteri appropriati. La base <xref:Microsoft.VisualStudio.Package.Methods> presuppone di classe c\#\-firma del metodo stile. Vedere la <xref:Microsoft.VisualStudio.Package.Methods> classe per informazioni dettagliate su come questa operazione può essere eseguita.  
  
## Abilita il supporto per le informazioni di parametro  
 Per supportare le descrizioni comandi informazioni sul parametro, è necessario impostare il `ShowCompletion` del parametro denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> a `true`. Il servizio di linguaggio legge il valore di questa voce del Registro di sistema dalla <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà.  
  
 Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> deve essere impostata su `true` per visualizzare la descrizione comando informazioni sul parametro.  
  
### Esempio  
 Ecco un esempio semplificato di rilevare i caratteri di elenco di parametri e l'impostazione attiva appropriato. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo. Nell'esempio di codice imposta semplicemente il trigger quando viene rilevato il tipo di carattere corretto.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## Supporto della descrizione comando informazioni di parametro nel Parser  
 La <xref:Microsoft.VisualStudio.Package.Source> classe viene assunto il contenuto di <xref:Microsoft.VisualStudio.Package.AuthoringScope> e <xref:Microsoft.VisualStudio.Package.AuthoringSink> classi quando la descrizione comando informazioni sul parametro viene visualizzata e aggiornata.  
  
-   Il parser ha <xref:Microsoft.VisualStudio.Package.ParseReason> quando viene digitato il carattere di inizio elenco di parametri.  
  
-   Il percorso specificato <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto viene immediatamente dopo che l'elenco di parametri carattere iniziale. Il parser deve raccogliere le firme di tutte le dichiarazioni di metodo disponibile all'indirizzo posizionare e archiviarle nella versione di un elenco di <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Questo elenco include il nome del metodo, tipo metodo \(o tipo restituito\) e un elenco di possibili parametri. Questo elenco viene eseguita la ricerca in un secondo momento per la firma del metodo o firme da visualizzare nella descrizione comando informazioni sul parametro.  
  
 Il parser deve analizzare la riga specificata da di <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per raccogliere il nome del metodo l'immissione e la distanza lungo l'utente si trova in digitando i parametri. Questa operazione viene eseguita passando il nome del metodo per il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metodo sul <xref:Microsoft.VisualStudio.Package.AuthoringSink> e quindi chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> viene analizzato il metodo quando l'elenco di parametri di avvio carattere, la chiamata di <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> metodo quando viene analizzato il carattere successivo elenco di parametri e infine chiamare il <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metodo quando viene analizzato il carattere di fine elenco di parametri. I risultati di queste chiamate al metodo vengono utilizzati per la <xref:Microsoft.VisualStudio.Package.Source> classe per aggiornare la descrizione comando informazioni sul parametro in modo appropriato.  
  
### Esempio  
 Ecco una riga di testo, che l'utente può immettere. I numeri sotto la linea indicano quale operazione viene effettuata dal parser in tale posizione nella riga \(presupponendo che l'analisi si sposta da sinistra a destra\). Il presupposto è che tutto ciò che precede la riga è già stato analizzato per le firme di metodo, tra cui la firma del metodo "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Di seguito è illustrata la procedura che accetta il parser:  
  
1.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con il testo "testfunc".  
  
2.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.