---
title: "Creating Custom T4 Text Template Directive Processors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 29
---
# Creating Custom T4 Text Template Directive Processors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel *processo di trasformazione di un modello di testo* viene preso un file *modello di testo* come input e viene generato un file di testo come output.  Il processo viene controllato dal *motore di trasformazione del modello di testo*, il quale interagisce inoltre con un host di trasformazione del modello di testo e uno o più *processori di direttiva* del modello di testo per completare il processo.  Per ulteriori informazioni, vedere [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Per creare un processore di direttiva personalizzato, si crea una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 La differenza tra queste due classi è che <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementa l'interfaccia minima necessaria a ottenere i parametri dall'utente e a generare il codice che produce il file di output del modello.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementa il modello di progettazione requires\/provides.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> gestisce due parametri speciali, `requires` e `provides`.  Ad esempio, un processore di direttiva personalizzato potrebbe accettare un nome file dall'utente, aprire e leggere il file, quindi archiviarne il testo in una variabile denominata `fileText`.  Una sottoclasse della classe <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> potrebbe prendere un nome file dall'utente come valore del parametro `requires` e il nome della variabile nella quale archiviare il testo come valore del parametro `provides`.  Questo processore aprirebbe e leggerebbe il file, quindi ne archivierebbe il testo nella variabile specificata.  
  
 Prima di chiamare un processore di direttiva personalizzato da un modello di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è necessario registrarlo.  
  
 Per ulteriori informazioni su come aggiungere una chiave del Registro di sistema, vedere [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md).  
  
## Direttive personalizzate  
 Una direttiva personalizzata ha un aspetto simile al seguente:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 È possibile utilizzare un processore di direttiva personalizzato quando si desidera accedere a dati o risorse esterni da un modello di testo.  
  
 Modelli di testo differenti possono condividere la funzionalità fornita da un singolo processore di direttiva, pertanto i processori di direttiva forniscono un modo per scomporre il codice per il riutilizzo.  La direttiva `include` incorporata è simile, perché può essere utilizzata per scomporre il codice e condividerlo fra modelli di testo diversi.  La differenza consiste nel fatto che qualsiasi funzionalità fornita dalla direttiva `include` è fissa e non accetta parametri.  Se si desidera fornire una funzionalità comune a un modello di testo e consentire al modello di passare dei parametri, è necessario creare un processore di direttiva personalizzato.  
  
 Alcuni esempi di processori di direttiva personalizzati potrebbero essere:  
  
-   Un processore di direttiva per la restituzione di dati da un database che accetta un nome utente e una password come parametri.  
  
-   Un processore di direttiva per l'apertura e la lettura di un file che accetta il nome del file come parametro.  
  
### Parti principali di un processore di direttiva personalizzato  
 Per sviluppare un processore di direttiva, è necessario creare una classe che eredita da <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 I metodi `DirectiveProcessor` più importanti che devono essere implementati sono i seguenti.  
  
-   `bool IsDirectiveSupported(string directiveName)`: restituisce `true` se il processore di direttiva può gestire la direttiva denominata.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)`: questo metodo viene chiamato dal motore del modello ad ogni occorrenza di una direttiva nel modello.  Il processore deve salvare i risultati.  
  
 Dopo tutte le chiamate a ProcessDirective\(\), il motore del modello chiamerà questi metodi:  
  
-   `string[] GetReferencesForProcessingRun()`: restituisce i nomi di assembly richiesti dal codice del modello.  
  
-   `string[] GetImportsForProcessingRun()`: restituisce gli spazi dei nomi che possono essere utilizzati nel codice del modello.  
  
-   `string GetClassCodeForProcessingRun()`: restituisce il codice di metodi, proprietà e altre dichiarazioni che il codice del modello può utilizzare.  Il modo più semplice per fare quanto indicato consiste nel compilare una stringa che contenga codice C\# o Visual Basic.  Per fare in modo che il processore di direttiva possa essere chiamato da un modello che utilizza un qualsiasi linguaggio CLR, è possibile creare le istruzioni come struttura ad albero CodeDom e restituire quindi il risultato della serializzazione della struttura ad albero nel linguaggio utilizzato dal modello.  
  
-   Per ulteriori informazioni, vedere [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## Argomenti della sezione  
 [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md)  
 Viene spiegato come registrare un processore di direttiva personalizzato.  
  
 [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Viene descritto come creare un processore di direttiva personalizzato, come registrare e testare il processore di direttiva e come formattare i file di output come HTML.