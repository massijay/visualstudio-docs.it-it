---
title: "CA3076: Esecuzione di script XSLT non protetta | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3076: Esecuzione di script XSLT non protetta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Categoria|Microsoft.Security|  
|Modifica importante|Non importante|  
  
## Causa  
 Se si esegue [Extensible Stylesheets Language Transformations \(XSLT\)](https://support.microsoft.com/en-us/kb/313997) in applicazioni .NET in modo non protetto, il processore può [risolvere i riferimenti URI non attendibili](http://msdn.microsoft.com/it-it/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) che potrebbero divulgare informazioni riservate a utenti malintenzionati causando attacchi Denial of Service e XSS.  
  
## Descrizione della regola  
 [XSLT](http://msdn.microsoft.com/it-it/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) è uno standard W3C \(World Wide Web Consortium\) per la trasformazione dei dati XML. XSLT viene in genere usato per scrivere i fogli di stile per trasformare i dati XML in altri formati, ad esempio HTML, testo di lunghezza fissa, testo delimitato da virgole, oppure in un altro formato XML. Sebbene non sia consentito per impostazione predefinita, è possibile scegliere di abilitarlo per un progetto.  
  
 Per garantire di non esporre una superficie di attacco, questa regola viene attivata ogni volta che XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> riceve una combinazione non protetta di istanze di <xref:System.Xml.Xsl.XsltSettings> e <xref:System.Xml.XmlResolver>, che consente l'elaborazione di script dannosi.  
  
## Come correggere le violazioni  
  
-   Sostituire l'argomento XsltSettings non protetto con XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con un'istanza che ha disabilitato l'esecuzione di script e funzioni del documento.  
  
-   Sostituire l'argomento <xref:System.Xml.XmlResolver> con Null o con un'istanza di <xref:System.Xml.XmlSecureResolver>.  
  
## Esclusione di avvisi  
 A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.  
  
## Esempi di pseudocodice  
  
### Violazione  
  
```c#  
using System.Xml;  
using System.Xml.Xsl;  
  
namespace TestNamespace   
{   
    class TestClass   
    {  
         void TestMethod()   
        {    
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
             var settings = XsltSettings.TrustedXslt;   
             var resolver = new XmlUrlResolver();   
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
        }  
    }   
}   
```  
  
### Soluzione  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        void TestMethod()   
        {   
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
            var settings = XsltSettings.Default;   
            var resolver = new XmlUrlResolver();   
            xslCompiledTransform.Load("testStylesheet", settings, resolver);   
        }   
    }   
}  
```  
  
### Violazione  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```  
  
### Soluzione  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                settings.EnableDocumentFunction = false;   
                settings.EnableScript = false;   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver);   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```