---
title: Supporto per la finestra Auto in un servizio di linguaggio Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
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
ms.openlocfilehash: 88cff53ca5c335fdf60aef85d79e9c6e86f03cfa
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Supporto per la finestra Auto in un servizio di linguaggio Legacy
Il **Auto** finestra vengono visualizzate le espressioni, ad esempio variabili e parametri che rientrano nell'ambito quando il programma in corso il debug viene sospesa (a causa di un punto di interruzione o un'eccezione). Le espressioni possono includere le variabili locali o globali e i parametri che sono stati modificati in ambito locale. Il **Auto** finestra può includere anche le istanze di una classe, struttura o un altro tipo. Tutto ciò che un analizzatore di espressioni può valutare potenzialmente può essere visualizzata nel **Auto** finestra.  
  
 Il framework di pacchetto gestito (MPF) è incluso alcun supporto diretto per il **Auto** finestra. Tuttavia, se esegue l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>(metodo), è possibile restituire un elenco delle espressioni devono essere presentati nel **Auto** finestra.</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementazione del supporto per la finestra Auto  
 È sufficiente per supportare il **Auto** finestra consiste nell'implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>metodo nella <xref:Microsoft.VisualStudio.Package.LanguageService>classe.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> L'implementazione deve decidere, specificando un percorso nel file di origine, le espressioni devono visualizzare nel **Auto** finestra. Il metodo restituisce un elenco di stringhe in cui ogni stringa rappresenta una singola espressione. Un valore restituito di <xref:Microsoft.VisualStudio.VSConstants.S_OK>indica che l'elenco contiene le espressioni, mentre <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>indica che non sono presenti espressioni da visualizzare.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
 Le espressioni effettive restituite sono nomi delle variabili o parametri che sono visualizzati in tale posizione nel codice. Questi nomi vengono passati l'analizzatore di espressioni per ottenere valori e i tipi che vengono quindi visualizzati di **Auto** finestra.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata un'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>metodo che ottiene un elenco di espressioni dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>metodo utilizzando il motivo di analisi <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Ogni espressione viene incluso come un `TestVsEnumBSTR` che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>interfaccia.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>  
  
 Si noti che il `GetAutoExpressionsCount` e `GetAutoExpression` sono descritti i metodi personalizzati nel `TestAuthoringSink` dell'oggetto e sono stati aggiunti per supportare questo esempio. Rappresentano uno dei modi in cui espressioni aggiunte al `TestAuthoringSink` oggetto dal parser (chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>metodo) sono accessibili all'esterno del parser.</xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>  
  
```c#  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```
