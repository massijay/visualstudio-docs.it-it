---
title: "CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Categoria|Microsoft.Security|  
|Modifica importante|Non importante|  
  
## Causa  
 Quando si progetta un'API derivata da XMLDocument e XMLTextReader, tenere presente <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Se si usano istanze di DTDProcessing non protette per fare riferimento o risolvere origini di entità esterne oppure per impostare valori non protetti nel codice XML, si può causare la divulgazione di informazioni.  
  
## Descrizione della regola  
 La [definizione DTD \(Document Type Definition\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) rappresenta uno dei due modi in cui un parser XML può determinare la validità di un documento, come definito dalla raccomandazione [W3C \(World Wide Web Consortium\) Extensible Markup Language \(XML\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori delle minacce potenziali di [Diffusione di informazioni](../Topic/Information%20Disclosure.md), che possono causare attacchi [Denial of Service \(DoS\)](../Topic/Denial%20of%20Service.md). Questa regola viene attivata quando:  
  
-   Le classi <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> usano valori resolver predefiniti per l'elaborazione DTD.  
  
-   Non è definito alcun costruttore per le classi derivate XmlDocument o XmlTextReader oppure non sono usati valori sicuri per <xref:System.Xml.XmlResolver>.  
  
## Come correggere le violazioni  
  
-   Rilevare ed elaborare tutte le eccezioni XmlTextReader correttamente per evitare la divulgazione di informazioni sul percorso.  
  
-   Usare l'oggetto <xref:System.Xml.XmlSecureResolver> al posto di XmlResolver per limitare le risorse a cui può accedere  XmlTextReader .  
  
## Esclusione di avvisi  
 A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.  
  
## Esempi di pseudocodice  
  
### Violazione  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass () {} // warn   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2() // warn   
        {   
        }   
    }   
}  
```  
  
### Soluzione  
  
```c#  
using System;   
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass : XmlDocument    
    {   
        public TestClass ()    
        {   
            XmlResolver = null;   
        }   
    }   
  
    class TestClass2 : XmlTextReader    
    {       
        public TestClass2()    
        {   
               XmlResolver = null;   
        }   
    }   
}  
```