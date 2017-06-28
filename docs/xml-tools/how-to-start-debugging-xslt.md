---
title: "Procedura: avvio del debug XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: avvio del debug XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debugger XSLT può essere utilizzato per eseguire il debug di un foglio di stile o di un'applicazione XSLT.Durante il debug è possibile eseguire il codice una riga alla volta eseguendo le istruzioni, ignorandole o eseguendole al di fuori del codice.I comandi per utilizzare la funzionalità di esecuzione del codice riga per riga sono uguali a quelli del debugger XSLT e degli altri debugger di Visual Studio.Una volta avviato il debug, nel debugger XSLT vengono aperte finestre di visualizzazione del documento di input e dell'output XSLT.  
  
## Editor XML  
 È possibile avviare il debugger dall'editor XML.Questo consente di eseguire il debug durante la progettazione di un foglio di stile.  
  
#### Per avviare il debug da un foglio di stile  
  
1.  Aprire il foglio di stile nell'editor XML.  
  
2.  Scegliere **Debug XSLT** dal menu **XML**.  
  
#### Per avviare il debug da un documento di input XML  
  
1.  Aprire il documento XML nell'editor XML.  
  
2.  Scegliere **Debug XSLT** dal menu **XML**.  
  
## XSLT di altre lingue  
 È possibile inoltre eseguire le istruzioni XSLT durante il debug di un'applicazione.Se si preme F11 su una chiamata <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName>, il debugger sarà in grado di eseguire il codice XSLT.  
  
> [!NOTE]
>  Non è supportata l'esecuzione di istruzioni XSLT dalla classe <xref:System.Xml.Xsl.XslTransform>.La classe <xref:System.Xml.Xsl.XslCompiledTransform> è l'unico processore XSLT in grado di supportare l'esecuzione di istruzioni XSLT durante il debug.  
  
#### Per avviare il debug di un'applicazione XSLT  
  
1.  Durante la creazione dell'istanza dell'oggetto <xref:System.Xml.Xsl.XslCompiledTransform>, impostare il parametro `enableDebug` su `true` nel codice.  
  
     In questo modo viene indicato al processore XSLT di creare le informazioni di debug dopo la compilazione del codice.  
  
2.  Premere F11 per eseguire il codice XSLT.  
  
     Il foglio di stile XSLT viene caricato in una nuova finestra di documento e il debugger XSLT viene avviato.  
  
     In alternativa, è possibile aggiungere un punto di interruzione al foglio di stile ed eseguire l'applicazione.  
  
### Esempio  
 Di seguito è riportato un esempio di programma XSLT in C\#.Viene illustrato come abilitare il debug di XSLT.  
  
```  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
  
namespace ConsoleApplication   
{  
  class Program   
  {  
    private const string sourceFile = @"c:\data\xsl_files\books.xml";  
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";  
    private const string outputFile = @"c:\data\xsl_files\output.xml";  
  
    static void Main(string[] args)  
    {  
      // Enable XSLT debugging.  
      XslCompiledTransform xslt = new XslCompiledTransform(true);  
  
      // Compile the style sheet.  
      xslt.Load(stylesheet)  
  
      // Execute the XSLT transform.  
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);  
      xslt.Transform(sourceFile, null, outputStream);  
    }  
  }  
}  
```  
  
## Vedere anche  
 [Procedura dettagliata: eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)   
 [Code Stepping Overview](http://msdn.microsoft.com/it-it/8791dac9-64d1-4bb9-b59e-8d59af1833f9)