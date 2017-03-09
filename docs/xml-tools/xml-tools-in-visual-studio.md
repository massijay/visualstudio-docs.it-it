---
title: "Strumenti XML in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "classi [Visual Studio], XML"
  - "CSS, fogli di stile per XML"
  - "dati [Visual Studio], XML"
  - "dataset [Visual Basic], XML Schema"
  - "file di individuazione, XML"
  - "Enterprise (modelli), XML e"
  - "controlli server, XML e"
  - "SGML, XML"
  - "fogli di stile, per XML"
  - "controlli server Web, XML"
  - "servizi Web"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], classi .NET Framework"
  - "XML [Visual Studio], origini dati"
  - "XML [Visual Studio], risorse"
  - "XML [Visual Studio], relazione SGML con"
  - "XML Schema"
  - "XMLDataDocument (classe)"
  - "XSD (schemi)"
  - "XSL"
  - "XSL, fogli di stile"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Strumenti XML in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Extensible Markup Language \(XML\)* è un linguaggio di markup che fornisce un formato per la descrizione dei dati.  Offre una maggiore precisione per le dichiarazioni del contenuto e risultati di ricerca più significativi tra più piattaforme.  Il linguaggio XML consente inoltre di separare la presentazione dai dati.  Ad esempio, in HTML si usano i tag per indicare al browser di visualizzare i dati in grassetto o corsivo. In XML invece si usano i tag solo per descrivere i dati, ad esempio nome della città, temperatura e pressione barometrica.  In XML si usano i fogli di stile, ad esempio XSL \(Extensible Stylesheet Language\) e CSS \(Cascading Style Sheet\) per presentare i dati in un browser.  XML separa i dati dalla presentazione e dall'elaborazione.  In questo modo è possibile presentare ed elaborare i dati come si vuole, applicando fogli di stile e applicazioni diversi.  
  
 XML è un sottoinsieme di SGML ottimizzato per la distribuzione sul Web.  È definito dal World Wide Web Consortium \(W3C\)  Questa standardizzazione garantisce che i dati strutturati siano uniformi e indipendenti da applicazioni o fornitori.  
  
 Molte funzionalità di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] sono basate su XML.  L'argomento seguente descrive gli strumenti e le funzionalità relativi a XML disponibili in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Per altre informazioni, vedere il [centro per sviluppatori XML](http://go.microsoft.com/fwlink/?LinkID=100176), in cui sono disponibili la documentazione più recente, informazioni tecniche, download, newsgroup e altre risorse per sviluppatori XML.  
  
## In questa sezione  
 [Utilizzo di dati XML](../xml-tools/working-with-xml-data.md)  
 Viene presentato il ruolo del linguaggio XML nel modo in cui sono gestiti in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Debug di fogli di stile XSLT \(Extensible Stylesheet Language Transformation\)](../xml-tools/debugging-xslt.md)  
 Fornisce collegamenti ad argomenti relativi all'uso del debugger di Visual Studio per eseguire il debug dei fogli di stile XSLT.  
  
## Riferimenti  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Espone l'albero di analisi dell'[editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) tramite [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) per qualsiasi documento.  
  
 [Riferimento agli standard XML](http://msdn.microsoft.com/it-it/79c78508-c9d0-423a-a00f-672e855de401)  
 Fornisce informazioni sulle tecnologie XML, ad esempio su XML, DTD \(Document Type Definition\), XSD \(linguaggio di definizione dello schema XML\) e fogli di stile XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Descrive le classi e altri elementi che costituiscono lo spazio dei nomi <xref:System.Xml> e fornisce collegamenti a informazioni dettagliate per ogni elemento.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Descrive le classi e altri elementi che costituiscono lo spazio dei nomi <xref:System.Xml.Serialization> e fornisce collegamenti a informazioni dettagliate per ogni elemento.  
  
## Sezioni correlate  
 [Modello DOM \(Document Object Model\) XML](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 Fornisce informazioni sulla conformità della classe <xref:System.Xml.XmlDocument> e delle relative classi associate alle specifiche di supporto dello spazio dei nomi del modello \(DOM\) W3C \(Core\) Level 1 e Level 2.  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/it-it/3029834c-a27e-4331-b7aa-711924062182)  
 Descrive come <xref:System.Xml.XmlReader> fornisce accesso ai dati XML non memorizzato nella cache, di tipo forward\-only di sola lettura tramite un flusso XML.  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/it-it/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Descrive come la classe <xref:System.Xml.XmlWriter> fornisce un modo per generare flussi XML non memorizzato nella cache e di tipo forward\-only e consente di compilare documenti XML conformi allo standard W3C.  
  
 [Trasformazioni XSLT](../Topic/XSLT%20Transformations.md)  
 Descrive il modo in cui la classe <xref:System.Xml.Xsl.XslCompiledTransform> implementa la raccomandazione XSLT 1.0.  
  
 [Elaborazione di dati XML con il modello di dati XPath](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 Descrive il modo in cui la classe <xref:System.Xml.XPath.XPathNavigator> può elaborare i dati XML archiviati in un oggetto <xref:System.Xml.XPath.XPathDocument> o <xref:System.Xml.XmlDocument>.  La classe <xref:System.Xml.XPath.XPathNavigator> è basata sul modello di dati XQuery 1.0 e XPath 2.0 e può essere usata per spostarsi tra i dati XML e per modificarli.  
  
 [SOM \(Schema Object Model\) XML](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 Descrive le classi usate per creare e modificare schemi XML, tramite una classe <xref:System.Xml.Schema.XmlSchema> che consente di caricare e modificare uno schema.