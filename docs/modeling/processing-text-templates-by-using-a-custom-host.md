---
title: "Processing Text Templates by using a Custom Host | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, in application or VS extension"
  - "text templates, custom directive hosts"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
caps.handback.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Processing Text Templates by using a Custom Host
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel *processo di trasformazione di un modello di testo* viene preso un file *modello di testo* come input e viene generato un file di testo come output.  È possibile chiamare il motore di trasformazione del testo da un'estensione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o da un'applicazione autonoma in esecuzione in un computer nel quale è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Tuttavia, è necessario fornire un *host del modello di testo*.  Questa classe connette il modello all'ambiente, trovando risorse quali gli assembly e i file di inclusione e gestendo l'output e i messaggi di errore.  
  
> [!TIP]
>  Se si scrive un pacchetto o un'estensione che verrà eseguita in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], anziché scrivere il proprio host, è consigliabile utilizzare il servizio del modello di testo.  Per ulteriori informazioni, vedere [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
> [!NOTE]
>  Si sconsiglia di utilizzare le trasformazioni del modello di testo nelle applicazioni server.  Si sconsiglia di utilizzare le trasformazioni del modello di testo eccetto in un thread singolo.  Questo perché il motore del modello di testo riutilizza un solo AppDomain per tradurre, compilare ed eseguire i modelli.  Il codice tradotto non è progettato per essere thread\-safe.  Il motore viene progettato per elaborare file in serie, come sono in fase di progettazione in un progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
>   
>  Per le applicazioni della fase di esecuzione, si consiglia di utilizzare modelli di testo pre\-elaborati: vedere [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Se l'applicazione utilizza un set di modelli corretti in fase di compilazione, sarà più facile utilizzare modelli di testo pre\-elaborati.  È possibile utilizzare questo approccio anche se l'applicazione sarà in esecuzione in un computer nel quale non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Esecuzione di un modello di testo nell'applicazione  
 Per eseguire un modello di testo, chiamare il metodo ProcessTemplate di <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 L'applicazione deve trovare e fornire il modello e deve gestire l'output.  
  
 Nel parametro `host`, è necessario fornire una classe che implementa <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  Questa viene richiamata dal motore.  
  
 L'host deve essere in grado di registrare errori, risolvere riferimenti agli assembly e ai file di inclusione, fornire un dominio dell'applicazione nel quale il modello possa essere eseguito e possa chiamare il processore adatto per ciascuna direttiva.  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> è definito in **Microsoft.VisualStudio.TextTemplating.\*.0.dll** e <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> è definito in **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll**.  
  
## Argomenti della sezione  
 [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 Viene mostrato come creare un host del modello di testo personalizzato che rende la funzionalità del modello di testo disponibile al di fuori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Riferimento  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## Sezioni correlate  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Viene illustrato il funzionamento della trasformazione di testo e quali parti è possibile personalizzare.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 Viene fornita una panoramica dei processori di direttiva del modello di testo.