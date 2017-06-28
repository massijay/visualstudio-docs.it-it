---
title: Richiamo della trasformazione del testo in un&quot;estensione di Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64674976-841f-43cb-8e61-0645c8a89eec
caps.latest.revision: 5
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: 0120e0adfed2c27ebd17d446f2f0e5c808acff92
ms.contentlocale: it-it
ms.lasthandoff: 02/22/2017

---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Richiamo della trasformazione del testo in un'estensione VS
Se si scrive un'estensione di Visual Studio, ad esempio un comando di menu o [linguaggio specifico di dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), è possibile utilizzare il servizio del modello di testo per trasformare i modelli di testo. Ottenere <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating>assistenza e di eseguirne il cast in <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> </xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating>  
  
## <a name="getting-the-text-templating-service"></a>Come ottenere il servizio del modello di testo  
  
```c#  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
  
// Process a text template:  
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));  
  
```  
  
## <a name="passing-parameters-to-the-template"></a>Passaggio dei parametri al modello  
 È possibile passare i parametri nel modello. Nel modello è possibile ottenere i valori dei parametri tramite la direttiva `<#@parameter#>`.  
  
 Per il tipo di un parametro, è necessario utilizzare un tipo serializzabile o di cui può essere effettuato il marshalling. Ovvero, il tipo deve essere dichiarato con <xref:System.SerializableAttribute>, o deve essere derivata da <xref:System.MarshalByRefObject>.</xref:System.MarshalByRefObject> </xref:System.SerializableAttribute> Questa restrizione è necessaria perché il modello di testo viene eseguito in un AppDomain separato. Tutti i tipi incorporati, ad esempio **System. String** e **System. Int32** sono serializzabili.  
  
 Per passare i valori dei parametri, il codice chiamante può inserire i valori nel `Session` dizionario, o in <xref:System.Runtime.Remoting.Messaging.CallContext>.</xref:System.Runtime.Remoting.Messaging.CallContext>  
  
 Nell'esempio seguente per trasformare un modello di testo breve vengono utilizzati entrambi i metodi:  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
using Microsoft.VisualStudio.TextTemplating.VSHost;  
...  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = dte;   
  
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;  
  
// Create a Session in which to pass parameters:  
sessionHost.Session = sessionHost.CreateSession();  
sessionHost.Session["parameter1"] = "Hello";  
sessionHost.Session["parameter2"] = DateTime.Now;  
  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);  
  
// Process a text template:  
string result = t4.ProcessTemplate("",  
   // This is the test template:  
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"  
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"  
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"  
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");  
  
// This test code yields a result similar to the following line:  
//     Test: Hello    07/06/2010 12:37:45    42  
  
```  
  
## <a name="error-reporting-and-the-output-directive"></a>Segnalazione errori e direttiva Output  
 Qualsiasi errore che si verifica durante l'elaborazione verrà visualizzato nella finestra di errore di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Inoltre, è possibile ricevere una notifica degli errori specificando un callback che implementa <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>.</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback>  
  
 Se si desidera scrivere la stringa di risultato in un file, è utile conoscere quale estensione di file e codifica sono state specificate nella direttiva `<#@output#>` del modello. Anche queste informazioni verranno passate al callback. Per ulteriori informazioni, vedere [direttiva Output T4](../modeling/t4-output-directive.md).  
  
```c#  
void ProcessMyTemplate(string MyTemplateFile)  
{  
  string templateContent = File.ReadAllText(MyTemplateFile);  
  T4Callback cb = new T4Callback();  
  // Process a text template:  
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);  
  // If there was an output directive in the MyTemplateFile,  
  // then cb.SetFileExtension() will have been called.  
  // Determine the output file name:  
  string resultFileName =   
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),   
        Path.GetFileNameWithoutExtension(MyTemplateFile))   
      + cb.fileExtension;  
  // Write the processed output to file:  
  File.WriteAllText(resultFileName, result, cb.outputEncoding);  
  // Append any error messages:  
  if (cb.errorMessages.Count > 0)  
  {  
    File.AppendAllLines(resultFileName, cb.errorMessages);  
  }  
}  
  
class T4Callback : ITextTemplatingCallback  
{  
  public List<string> errorMessages = new List<string>();  
  public string fileExtension = ".txt";  
  public Encoding outputEncoding = Encoding.UTF8;  
  
  public void ErrorCallback(bool warning, string message, int line, int column)  
  { errorMessages.Add(message); }  
  
  public void SetFileExtension(string extension)  
  { fileExtension = extension; }  
  
  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)  
  { outputEncoding = encoding; }  
}  
  
```  
  
 Il codice può essere testato con un file modello simile a quello seguente:  
  
```  
<#@output extension=".htm" encoding="ASCII"#>  
<# int unused;  // Compiler warning "unused variable"  
#>  
Sample text.  
```  
  
 L'avviso del compilatore verrà visualizzato nella finestra di errore di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e genererà inoltre una chiamata a `ErrorCallback`.  
  
## <a name="reference-parameters"></a>Parametri per riferimento  
 È possibile passare i valori da un modello di testo utilizzando una classe di parametri derivata da <xref:System.MarshalByRefObject>.</xref:System.MarshalByRefObject>  
  
## <a name="related-topics"></a>Argomenti correlati  
 Per generare testo da un modello di testo pre-elaborato:  
 Chiamare il metodo `TransformText()` della classe generata. Per ulteriori informazioni, vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Per generare testo all'esterno di un'estensione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
 Definire un host personalizzato. Per ulteriori informazioni, vedere [l'elaborazione di modelli di testo tramite un Host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 Per generare codice sorgente che può essere compilato ed eseguito in un secondo momento:  
 Chiamare il `t4.PreprocessTemplate()` <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.</xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> (metodo)
