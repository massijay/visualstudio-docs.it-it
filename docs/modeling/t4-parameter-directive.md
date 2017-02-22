---
title: "T4 Parameter Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Parameter Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In un modello di testo di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la direttiva `parameter` dichiara le proprietà nel codice del modello inizializzate dai valori passati dal contesto esterno.  È possibile impostare questi valori se si scrive codice che richiama la trasformazione del testo.  
  
## Utilizzo della direttiva Parameter  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 La direttiva `parameter` dichiara le proprietà nel codice del modello inizializzate dai valori passati dal contesto esterno.  È possibile impostare questi valori se si scrive codice che richiama la trasformazione del testo.  È possibile passare i valori nel dizionario `Session` o in <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 È possibile dichiarare i parametri di qualsiasi tipo utilizzabile in remoto.  In altri termini, è necessario dichiarare il tipo con <xref:System.SerializableAttribute> oppure deve derivare da <xref:System.MarshalByRefObject>.  In questo modo i valori dei parametri vengano passati nell'AppDomain in cui viene elaborato il modello.  
  
 Ad esempio, è possibile scrivere un modello di testo con il contenuto seguente:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## Passaggio dei valori dei parametri in un modello  
 Se si scrive un'estensione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quale un comando di menu o un gestore eventi, è possibile elaborare un modello tramite il servizio del modello di testo:  
  
```c#  
// Get a service provider – how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## Passaggio di valori nel contesto di chiamata  
 In alternativa, è possibile passare valori come dati logici in <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Nell'esempio seguente i valori vengono passati utilizzando entrambi i metodi:  
  
```c#  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## Passaggio di valori a un modello di testo \(pre\-elaborato\) della fase di esecuzione  
 Non è di solito necessario utilizzare la direttiva `<#@parameter#>` con i modelli di testo \(pre\-elaborati\) della fase di esecuzione.  Al contrario, è possibile definire un costruttore aggiuntivo o una proprietà impostabile per il codice generato tramite il quale vengono passati i valori dei parametri.  Per ulteriori informazioni, vedere [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Tuttavia, se si desidera utilizzare `<#@parameter>` in un modello della fase di esecuzione, è possibile passare i valori a tale modello tramite il dizionario Session.  Si supponga ad esempio di avere creato il file come modello pre\-elaborato denominato `PreTextTemplate1`.  È possibile richiamare il modello nel programma tramite il codice seguente.  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## Acquisizione di argomenti da TextTemplate.exe  
  
> [!IMPORTANT]
>  La direttiva `parameter` non recupera valori impostati nel parametro `–a` dell'utilità `TextTransform.exe`.  Per ottenere tali valori, impostare `hostSpecific="true"` nella direttiva `template` e utilizzare `this.Host.ResolveParameterValue("","","argName")`.