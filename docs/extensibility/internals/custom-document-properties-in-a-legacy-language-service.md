---
title: "Propriet&#224; personalizzate dei documenti in un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "proprietà personalizzate dei documenti servizi linguistici [framework pacchetto gestito]"
  - "proprietà del documento, personalizzata"
  - "servizi di linguaggio [framework gestito pacchetto], proprietà personalizzate del documento"
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Propriet&#224; personalizzate dei documenti in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le proprietà del documento possono essere visualizzati nella finestra di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**Proprietà** .  I linguaggi di programmazione non presentano in genere proprietà associate ai singoli file di origine. Tuttavia, supporta XML vengono illustrate le proprietà che influiscono sulla codifica, lo schema e il foglio di stile.  
  
## Descrizione  
 Se il linguaggio sono necessarie le proprietà personalizzate del documento, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.DocumentProperties> e distribuire le proprietà necessarie nella classe derivata.  
  
 Inoltre, le proprietà del documento in genere archiviate nel file di origine stesso.  Questo richiede al servizio di linguaggio di analizzare le informazioni delle proprietà dal file di origine per visualizzare nella finestra di **Proprietà** e aggiornare il file di origine quando viene apportata una modifica alle proprietà del documento nella finestra di **Proprietà** .  
  
## personalizzare la classe di DocumentProperties  
 Per supportare le proprietà personalizzate del documento, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.DocumentProperties> e aggiungere il numero di proprietà necessari.  È inoltre necessario fornire gli attributi dell'utente per organizzarle nella finestra di **Proprietà** .  Se una proprietà dispone solo di una funzione di accesso di `get` , viene visualizzata come di sola lettura nella finestra di **Proprietà** .  If a property has both `get` and `set` accessors, the property can also be updated in the **Properties** window.  
  
### Esempio  
 In questo caso è una classe di esempio derivata da <xref:Microsoft.VisualStudio.Package.DocumentProperties>, mostrando due proprietà, nome file e descrizioni.  Quando una proprietà viene aggiornata, un metodo personalizzato nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> viene chiamato per scrivere la proprietà al file di origine.  
  
```c#  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## Creare un'istanza di una classe personalizzata di DocumentProperties  
 Per creare un'istanza della classe di proprietà personalizzate del documento, è necessario eseguire l'override del metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> nella versione della classe di <xref:Microsoft.VisualStudio.Package.LanguageService> per restituire una sola istanza della classe di <xref:Microsoft.VisualStudio.Package.DocumentProperties> .  
  
### Esempio  
  
```c#  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## Proprietà nel file di origine  
 Poiché le proprietà del documento sono generalmente specifiche del file di origine, i valori vengono archiviati nel file di origine stesso.  Questo richiede il supporto dal parser o dallo scanner di linguaggio di definire tali proprietà.  Ad esempio, le proprietà di un documento XML vengono archiviati sul nodo radice.  I valori sul nodo radice quando vengono modificati i valori della finestra di **Proprietà** vengono modificati e il nodo radice viene aggiornato nell'editor.  
  
### Esempio  
 In questo esempio vengono archiviati le proprietà “nomefile„ e “struttura„ nelle prime due righe del file di origine, incorporate in un'intestazione di commento speciale, ad esempio:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 Questo esempio mostra i due metodi necessari per ottenere e impostare le proprietà del documento dalle prime due righe del file di origine e come le proprietà vengono aggiornate se l'utente modifica direttamente il file di origine.  Il metodo di `SetPropertyValue` nell'esempio riportato di seguito è quello chiamato dalla classe di `TestDocumentProperties` come in l “che personalizza la sezione della classe di DocumentProperties„.  
  
 In questo esempio viene utilizzato lo scanner per determinare il tipo di token nelle prime due righe.  Questo esempio è solo a titolo esemplificativo.  Un approccio più comune a questa situazione è di analizzare il file di origine in quanto viene chiamato una struttura ad albero di traccia in cui ogni nodo della struttura ad albero contiene informazioni su un token specifico.  Il nodo radice contiene le proprietà del documento.  
  
```c#  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Vedere anche  
 [Funzionalità del linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)