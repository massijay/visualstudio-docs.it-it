---
title: "La struttura in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "struttura"
  - "servizi di linguaggio [framework gestito pacchetto], la struttura"
  - "la struttura, supporto in servizi di linguaggio [framework pacchetto gestito]"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# La struttura in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Struttura consente di comprimere un programma complesso in una panoramica o struttura. Ad esempio, in c\# tutti i metodi possono essere compressi in una singola riga, che mostra solo la firma del metodo. Inoltre, strutture e classi possono essere compresse per mostrare solo i nomi delle classi e strutture. All'interno di un singolo metodo, una logica complessa può essere compresso per mostrare il flusso generale mostrando solo la prima riga di istruzioni, ad esempio `foreach`, `if`, e `while`.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Abilita il supporto per la struttura  
 Il `AutoOutlining` voce del Registro di sistema è impostato su 1 per abilitare la struttura automatica. La struttura automatica consente di impostare un'analisi dell'intera origine quando un file viene caricato o modificato per identificare aree nascoste e visualizzare le icone della struttura. Struttura possa essere controllata anche manualmente dall'utente.  
  
 Il valore di `AutoOutlining` voce del Registro di sistema può essere ottenuto tramite la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Il `AutoOutlining` voce del Registro di sistema può essere inizializzati con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo \(vedere [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate\).  
  
## L'area nascosta  
 Per fornire la struttura, il servizio di linguaggio deve supportare aree nascoste. Questi sono gli intervalli di testo che può essere espanso o compresso. Aree nascoste possono essere delimitate dai simboli di linguaggio standard, ad esempio le parentesi graffe, oppure i simboli personalizzati. Ad esempio, c\# ha un `#region`\/`#endregion` coppia che delimita un'area nascosta.  
  
 Aree nascoste sono gestite da un responsabile di area nascosta, che viene esposto come il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaccia.  
  
 La struttura utilizza aree nascoste di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> l'interfaccia e contengono l'intervallo tra l'area nascosta, lo stato di visualizzazione corrente e l'intestazione da visualizzare quando l'intervallo è compressa.  
  
 Il parser di linguaggio servizio utilizza il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo per aggiungere una nuova regione nascosta con il comportamento predefinito per le aree nascoste, mentre il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo consente di personalizzare l'aspetto e comportamento della struttura. Una volta aree nascoste vengono assegnate per la sessione di area nascosta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le aree nascoste per il servizio di linguaggio.  
  
 Se è necessario determinare quando viene eliminata la sessione di area nascosta, viene modificata in un'area nascosta oppure è necessario assicurarsi che una determinata area nascosta è visibile; è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override dei metodi appropriati, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, rispettivamente.  
  
### Esempio  
 Ecco un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio fornisce corrispondenza parentesi graffe e le parentesi graffe devono corrispondere includano almeno le parentesi graffe \({e}\). Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una gestione completa dei case in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. In questo esempio viene inoltre illustrato come impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferenza a `true` temporaneamente. In alternativa è possibile specificare il `AutoOutlining` parametro denominato nella `ProvideLanguageServiceAttribute` attributo nel pacchetto di linguaggio.  
  
 In questo esempio si presuppone che le regole di c\# per i commenti, stringhe e valori letterali.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
  
    public class MyLanguageService : LanguageService  
    {  
        private LanguagePreferences m_preferences;  
  
        public override LanguagePreferences  GetLanguagePreferences()  
        {  
            if (m_preferences == null)  
            {  
                m_preferences = new LanguagePreferences(this.Site,  
                                                        typeof(MyLanguageService).GUID,  
                                                        Name);  
                m_preferences.Init();  
                // Temporarily enabled auto-outlining  
                m_preferences.AutoOutlining = true;  
            }  
            return m_preferences;  
        }  
  
        public override AuthoringScope  ParseSource(ParseRequest req)  
        {  
            Source source = (Source) this.GetSource(req.FileName);  
            switch (req.Reason)  
            {  
               case ParseReason.HighlightBraces:  
               case ParseReason.MatchBraces:  
               case ParseReason.MemberSelectAndHighlightBraces:  
                  if (source.Braces != null)  
                  {  
                      foreach (TextSpan[] brace in source.Braces)  
                      {  
                         if (brace.Length == 2)  
                         {  
                             if (req.Sink.HiddenRegions == true   
                                   && source.GetText(brace[0]).Equals("{")   
                                   && source.GetText(brace[1]).Equals("}"))  
                             {  
                                //construct a TextSpan of everything between the braces  
                                TextSpan hideSpan = new TextSpan();  
                                hideSpan.iStartIndex = brace[0].iStartIndex;  
                                hideSpan.iStartLine = brace[0].iStartLine;  
                                hideSpan.iEndIndex = brace[1].iEndIndex;  
                                hideSpan.iEndLine = brace[1].iEndLine;  
                                req.Sink.ProcessHiddenRegions = true;  
                                req.Sink.AddHiddenRegion(hideSpan);  
                             }  
                             req.Sink.MatchPair(brace[0], brace[1], 1);  
                         }  
                         else if (brace.Length >= 3)  
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);  
                  }  
        }  
                   break;  
               default:  
                   break;  
      }  
            // Must always return a valid AuthoringScope object.  
            return new MyAuthoringScope();  
        }  
    }  
}  
```  
  
## Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)