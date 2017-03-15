---
title: Convalida i punti di interruzione in un servizio di linguaggio Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
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
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Convalida i punti di interruzione in un servizio di linguaggio Legacy
Un punto di interruzione indica che l'esecuzione del programma deve essere interrotta in un particolare punto mentre è in esecuzione in un debugger. Un utente può inserire un punto di interruzione su una qualsiasi riga nel file di origine, poiché l'editor non dispone di alcuna conoscenza di ciò che costituisce un percorso valido per un punto di interruzione. Quando il debugger viene avviato, tutti i punti di interruzione contrassegnate (denominati in sospeso i punti di interruzione) sono associati al percorso appropriato nel programma in esecuzione. Allo stesso tempo che i punti di interruzione vengono convalidate per assicurarsi che fungono da indicatore percorsi di codice valido. Ad esempio, un punto di interruzione in un commento non è valido, perché non esiste alcun codice in tale posizione nel codice sorgente. Il debugger disabilita i punti di interruzione non validi.  
  
 Poiché il servizio di linguaggio conosce il codice sorgente viene visualizzato, è possibile convalidare i punti di interruzione prima che il debugger viene avviato. È possibile eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>per restituire un intervallo che specifica un percorso valido per un punto di interruzione.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Del punto di interruzione viene comunque convalidato quando il debugger viene avviato, ma l'utente viene informato dei punti di interruzione non validi senza attendere che il debugger carichi.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementazione del supporto per la convalida dei punti di interruzione  
  
-   Il <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>metodo riceve la posizione del punto di interruzione.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> L'implementazione deve decidere se il percorso è valido e indicare questa opzione per la restituzione di un intervallo di testo che identifica il codice associato alla posizione riga del punto di interruzione.  
  
-   Restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>Se il percorso sia valido, o <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>Se non è valido.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
-   Se il punto di interruzione è valido e il punto di interruzione viene evidenziata l'intervallo di testo.  
  
-   Se il punto di interruzione non è valido, nella barra di stato viene visualizzato un messaggio di errore.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrata un'implementazione di <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>metodo che chiama il parser per ottenere l'intervallo di codice (se presente) nella posizione specificata.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>  
  
 Questo esempio si presuppone che sia stato aggiunto un `GetCodeSpan` metodo per la <xref:Microsoft.VisualStudio.Package.AuthoringSink>classe che convalida l'intervallo di testo e restituisce `true` in caso di un punto di interruzione valido.</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
```c#  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
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
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
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
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
