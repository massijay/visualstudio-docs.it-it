---
title: La formattazione di codice in un servizio di linguaggio Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
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
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>La formattazione di codice in un servizio di linguaggio Legacy

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile riformattare il codice sorgente da normalizzare l'utilizzo di spazi vuoti e i rientri. Può trattarsi di inserimento o rimozione spazi o tabulazioni all'inizio di ogni riga, aggiungere nuove righe tra le righe o la sostituzione degli spazi con schede con spazi o tabulazioni.  
  
>**Nota:** inserimento o eliminazione di caratteri di nuova riga può hanno effetto sulle indicatori, ad esempio punti di interruzione e i segnalibri, ma aggiungendo o rimuovendo spazi o tabulazioni non marcatori.  
  
Gli utenti possono avviare un'operazione riformattando selezionando **la selezione del formato** o **Formatta documento** dal **avanzate** menu la **modificare** menu. Un'operazione riformattando può essere attivata anche quando viene inserito un frammento di codice o un carattere specifico. Ad esempio, quando si digita una parentesi graffa di chiusura in c#, tutti gli elementi tra parentesi graffa di chiusura e la corrispondente parentesi graffa aperta viene rientrato automaticamente per il livello appropriato.
  
Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] invia il **la selezione del formato** o **Formatta documento** comando per il servizio di linguaggio, la <xref:Microsoft.VisualStudio.Package.ViewFilter>classe chiama il <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>metodo nella <xref:Microsoft.VisualStudio.Package.Source>classe.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> Per supportare la formattazione è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>metodo e specificare una formattazione di codice.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>Abilita il supporto per la formattazione  

Per supportare la formattazione, il `EnableFormatSelection` parametro il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>deve essere impostato su `true` quando si registra il pacchetto Visual Studio.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>proprietà `true`.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> Il <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>metodo restituisce il valore di questa proprietà.</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Se restituisce true, la <xref:Microsoft.VisualStudio.Package.ViewFilter>classe chiama <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
## <a name="implementing-reformatting"></a>Implementazione di riformattazione

Per implementare la riformattazione, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.Source>classe ed eseguire l'override di <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>(metodo).</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> L' <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>oggetto descrive l'estensione di formato e l' <xref:Microsoft.VisualStudio.Package.EditArray>oggetto contiene le modifiche apportate nell'intervallo</xref:Microsoft.VisualStudio.Package.EditArray> </xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Si noti che questo intervallo può essere l'intero documento. Tuttavia, poiché esistono probabilmente più le modifiche apportate all'intervallo, tutte le modifiche devono essere reversibile in un'unica azione. A tale scopo, eseguire il wrapping di tutte le modifiche in un <xref:Microsoft.VisualStudio.Package.CompoundAction>dell'oggetto (vedere la sezione "Utilizzo della classe CompoundAction" in questo argomento).</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>Esempio  

Nell'esempio seguente si che è uno spazio dopo ogni virgola nella selezione, a meno che la virgola seguita da una tabulazione o alla fine della riga. Gli spazi finali dopo l'eliminazione dell'ultima virgola in una riga. Vedere la sezione "Utilizzo della classe CompoundAction" in questo argomento per vedere come questo metodo viene chiamato dal <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>(metodo).</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Utilizzo della classe CompoundAction  
 
La riformattazione eseguita su una sezione di codice deve essere reversibile in un'unica azione. Questo può essere eseguita utilizzando una <xref:Microsoft.VisualStudio.Package.CompoundAction>classe.</xref:Microsoft.VisualStudio.Package.CompoundAction> Questa classe esegue il wrapping di un set di operazioni di modifica nel buffer di testo in un'operazione singola modifica.  
  
### <a name="example"></a>Esempio

Di seguito è riportato un esempio di come utilizzare la <xref:Microsoft.VisualStudio.Package.CompoundAction>classe.</xref:Microsoft.VisualStudio.Package.CompoundAction> Vedere l'esempio nella sezione "Implementazione di supporto per la formattazione" in questo argomento per un esempio di `DoFormatting` metodo.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Vedere anche

[Funzionalità del linguaggio legacy](legacy-language-service-features1.md)
