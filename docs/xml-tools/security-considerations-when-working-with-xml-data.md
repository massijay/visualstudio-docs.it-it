---
title: "Considerazioni sulla sicurezza durante l&#39;utilizzo di dati XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Considerazioni sulla sicurezza durante l&#39;utilizzo di dati XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono illustrati i problemi di sicurezza che è necessario prendere in considerazione quando si utilizza l'editor XML o il debugger XSLT.  
  
## Editor XML  
 L'editor XML è basato sull'editor di testo di Visual Studioe si basa sulle classi <xref:System.Xml> e <xref:System.Xml.Xsl> per gestire gran parte dei processi XML.  
  
-   Le trasformazioni XSLT vengono eseguite in un nuovo dominio applicazione.Le trasformazioni XSLT sono *sandboxed*: questo significa che vengono utilizzati i criteri di sicurezza dall'accesso al codice del computer per determinare le autorizzazioni limitate in base alla posizione in cui si trova il foglio di stile XSLT.Ad esempio, per i fogli di stile provenienti da un'area Internet vengono applicate autorizzazioni con la limitazione massima, mentre per i fogli di stile copiati sull'unità disco rigido del computer vengono eseguiti con un livello di Attendibilità totale.  
  
-   La classe <xref:System.Xml.Xsl.XslCompiledTransform> viene utilizzata per compilare il codice XSLT in Microsoft Intermediate Language per ottenere prestazioni più veloci durante l'esecuzione.  
  
-   Gli schemi che fanno riferimento a un percorso esterno nel file del catalogo vengono scaricati automaticamente quando l'editor XML viene caricato.La classe <xref:System.Xml.Schema.XmlSchemaSet> è utilizzata per compilare gli schemi.Il file del catalogo fornito con l'editor XML non dispone di collegamenti a schemi esterni.L'utente deve aggiungere in modo esplicito un riferimento allo schema esterno prima che l'editor XML scarichi il file di schema.È possibile disabilitare il download HTTP dalla pagina **Miscellaneous Tools Options** dell'editor XML.  
  
-   L'editor XML utilizza le classi <xref:System.Net> per scaricare gli schemi  
  
## Debugger XSLT  
 Il debugger XSLT utilizza il motore di debug gestito di Visual Studio e le classi degli spazi dei nomi <xref:System.Xml> e <xref:System.Xml.Xsl>.  
  
-   Il debugger XSLT esegue ogni trasformazione XSLT in un dominio applicazione sandboxed.I criteri di sicurezza dall'accesso di codice del computer vengono utilizzati per determinare le autorizzazioni limitate basate sulla posizione del foglio di stile XSLT.Ad esempio, per i fogli di stile provenienti da un'area Internet vengono applicate autorizzazioni con la limitazione massima, mentre per i fogli di stile copiati sull'unità disco rigido del computer vengono eseguiti con un livello di Attendibilità totale.  
  
-   Il foglio di stile XSLT viene compilato utilizzando la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   L'analizzatore di espressioni XSLT viene caricato dal motore di debug gestito.Il motore di debug gestito presuppone che tutto il codice venga eseguito dal computer locale dell'utente.Di conseguenza, la classe <xref:System.Xml.Xsl.XslCompiledTransform> scarica il file XSLT nel computer locale dell'utente.La possibilità che possa verificarsi un'elevazione dei privilegi di esecuzione è attenuata dall'esecuzione di tutte le trasformazioni XSLT in un nuovo dominio applicazione con autorizzazioni limitate.  
  
## Vedere anche  
 [Application Domains](http://msdn.microsoft.com/it-it/39e57d07-a740-4cd4-ae82-e119ea3856c1)