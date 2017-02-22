---
title: "Accessing Visual Studio or other Hosts from a Text Template | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 5
caps.handback.revision: 5
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Accessing Visual Studio or other Hosts from a Text Template
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In un modello di testo, è possibile utilizzare i metodi e le proprietà esposti dall'host che esegue il modello, ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Questo vale per i modelli di testo normali, non per i modelli di testo pre\-elaborati.  
  
## Come ottenere l'accesso all'host  
 Impostare `hostspecific="true"` nella direttiva `template`.  In questo modo è possibile utilizzare `this.Host`, che è di tipo <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>.  Questo tipo dispone di membri che è possibile utilizzare ad esempio per risolvere nomi di file e per registrare errori.  
  
### Risoluzione di nomi di file  
 Per trovare il percorso completo di un file relativo al modello di testo, utilizzare this.Host.ResolvePath \(\).  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.IO" #>  
<#  
 // Find a path within the same project as the text template:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
### Visualizzazione dei messaggi di errore  
 In questo esempio vengono registrati i messaggi quando il modello viene trasformato.  Se l'host è [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], i messaggi vengono aggiunti alla finestra di errore.  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="System.CodeDom.Compiler" #>  
<#  
  string message = "test message";  
  this.Host.LogErrors(new CompilerErrorCollection()   
    { new CompilerError(  
       this.Host.TemplateFile, // Identify the source of the error.  
       0, 0, "0",   // Line, column, error ID.  
       message) }); // Message displayed in error window.  
#>  
  
```  
  
## Utilizzo dell'API di Visual Studio  
 Se si esegue un modello di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile utilizzare `this.Host` per accedere ai servizi forniti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e a qualsiasi pacchetto o estensione caricati.  
  
 Impostare hostspecific \= "true" e cast `this.Host` su <xref:System.IServiceProvider>.  
  
 In questo esempio viene ottenuta l'API di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:EnvDTE.DTE> come servizio:  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#   
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
```  
  
## Utilizzo di hostSpecific con l'ereditarietà del modello  
 Specificare `hostspecific="trueFromBase"` se si utilizza anche il `inherits` attributo, e se si eredita da un modello che specifichi `hostspecific="true"`.  Questo consente di evitare un avviso del compilatore per l'effetto che la proprietà `Host` è stata dichiarata due volte.