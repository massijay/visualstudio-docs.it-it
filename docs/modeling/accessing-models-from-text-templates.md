---
title: "Accesso ai modelli da modelli di testo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di testo, accesso a modelli"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# Accesso ai modelli da modelli di testo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite i modelli di testo, è possibile creare i file di report, i file di codice sorgente e altri file di testo basati sui modelli di linguaggio specifico di dominio.  Per informazioni di base sui modelli di testo, vedere [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md).  I modelli di testo verranno eseguiti in modalità sperimentale quando si esegue il debug di DSL e anche funzioneranno in un computer in cui è stato distribuito il modello DSL.  
  
> [!NOTE]
>  Quando si crea una soluzione DSL, campionamento il modello di testo **\*.tt** i file vengono generati nel progetto di debug.  Quando si modificano i nomi delle classi di dominio, questi modelli non funzioneranno più.  Tuttavia, includono le direttive di base necessari e vengono forniti esempi che è possibile aggiornare in base al linguaggio DSL.  
  
 Per accedere a un modello da un modello di testo:  
  
-   Impostare la proprietà di eredità della direttiva del modello a <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>.  Ciò consente di accedere all'archivio.  
  
-   Specificare i processori di direttiva del modello DSL cui si desidera accedere.  Verranno caricati gli assembly per il linguaggio DSL in modo da poter utilizzare le classi di dominio, proprietà e relazioni nel codice del modello di testo.  Anche carica il file di modello specificato.  
  
 In `.tt` il file simile all'esempio seguente viene creato nel progetto di debug quando si crea un nuovo  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione dal modello minimo del linguaggio DSL.  
  
```  
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ output extension=".txt" #>  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
  
This text will be output directly.  
  
This is the name of the model: <#= this.ModelRoot.Name #>  
  
Here is a list of elements in the model:  
<#  
  // When you change the DSL Definition, some of the code below may not work.  
  foreach (ExampleElement element in this.ExampleModel.Elements)  
  {#>  
<#= element.Name #>  
<#      
  }  
#>  
  
```  
  
 Tenere presenti le informazioni seguenti su questo modello:  
  
-   Il modello può utilizzare le classi di dominio, le proprietà e le relazioni che è definito nella definizione di modello DSL.  
  
-   Il modello carica il file di modello specificato in `requires` proprietà.  
  
-   Una proprietà in `this` contiene l'elemento radice.  Dalla, il codice può passare ad altri elementi del modello.  Il nome della proprietà è in genere lo stesso della classe del dominio radice del modello DSL.  In questo esempio, viene `this.ExampleModel`.  
  
-   Sebbene il linguaggio in cui i frammenti di codice sono scritti in c\#, è possibile generare testo di qualsiasi tipo.  In alternativa è possibile scrivere il codice in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aggiunta della proprietà  `language="VB"` in  `template` direttiva.  
  
-   Per eseguire il debug del modello, aggiungere `debug="true"` in  `template` direttiva.  Il modello viene aperto in un'altra istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se si verifica un'eccezione.  Se si desidera interrompere il debugger a un punto specifico nel codice, inserire l'istruzione `System.Diagnostics.Debugger.Break();`  
  
     Per ulteriori informazioni, vedere [Debugging a T4 Text Template](../modeling/debugging-a-t4-text-template.md).  
  
## Sul processore di direttiva DSL  
 Il modello può utilizzare le classi di dominio che è definito nella definizione di modello DSL.  Ciò è determinata da una direttiva che in genere viene visualizzata accanto all'inizio del modello.  Nell'esempio precedente, è il seguente.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Il nome della direttiva \( `MyLanguage`, in questo esempio\) è derivato dal nome del modello DSL.  Richiama un oggetto *processore di direttiva* che viene generato come parte del modello DSL.  È possibile trovare il codice sorgente in **Dsl\\GeneratedCode\\DirectiveProcessor.cs**.  
  
 Il processore di direttiva DSL esegue due attività principali:  
  
-   Consente di inserire direttive di importazione e dell'assembly nel modello che fa riferimento al linguaggio DSL.  Ciò consente di utilizzare classi di dominio nel codice del modello.  
  
-   Carica il file specificati in `requires` parametro e impostare una proprietà in  `this` che fa riferimento all'elemento radice del modello caricato.  
  
## La convalida del modello prima di eseguire il modello  
 È possibile che il modello venga convalidato prima che il modello venga eseguito.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Notare che:  
  
1.  `filename` e  `validation` i parametri sono separati da “; „ e non devono essere presenti altri separatori o spazi.  
  
2.  L'elenco delle categorie di convalida determina i metodi di convalida vengono eseguiti.  Le categorie più devono essere separate con “&#124;„ e non devono essere presenti altri separatori o spazi.  
  
 Se viene rilevato un errore, verrà riportato nella finestra di errore e il file di risultati includerà un messaggio di errore.  
  
##  <a name="Multiple"></a> Accedere ai modelli di più di un modello di testo  
  
> [!NOTE]
>  Questo metodo consente di leggere modelli in stesso modello ma non supporta i riferimenti ModelBus.  Per leggere modelli collegati dai riferimenti ModelBus, vedere [Utilizzo di ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Se si desidera accedere più di un modello dallo stesso modello di testo, è necessario chiamare il processore di direttiva generato una volta per ciascun modello.  È necessario specificare il nome di ogni modello in `requires` parametro.  È necessario specificare i nomi che si desidera utilizzare per la classe di dominio radice in `provides` parametro.  È necessario specificare valori diversi per `provides` parametri in ognuna delle chiamate alla direttiva.  Ad esempio, si supponga di avere tre file di modello chiamati Library.xyz, School.xyz e Work.xyz.  Per accedervi dallo stesso modello di testo, è necessario creare tre chiamate alla direttiva simili ai seguenti.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Questo codice di esempio è valido per un linguaggio basato sul modello minimo della soluzione del linguaggio.  
  
 Per accedere ai modelli in un modello di testo, è possibile scrivere ora il codice simile al codice nell'esempio seguente.  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## Modelli di caricamento dinamico  
 Se si desidera determinare in fase di esecuzione i modelli caricare, è possibile caricare un file di modello nel codice del programma, anziché utilizzare la direttiva DSL\-specifica.  
  
 Tuttavia, una delle funzioni della direttiva DSL\-specifica è di importare lo spazio dei nomi DSL, in modo che il codice del modello può utilizzare le classi di dominio definite in tale modello DSL.  Poiché non si utilizza la direttiva, è necessario aggiungere **\<assembly\>** e  **\<import\>** direttive per tutti i modelli che è possibile caricare.  Ciò è agevole se i modelli diversi che è possibile caricare sono tutte le istanze dello stesso modello DSL.  
  
 Per caricare il file, il metodo più efficace consiste nell'utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus.  in uno scenario tipico, il modello di testo utilizzerà una direttiva DSL\-specifica per caricare il primo modello come sempre.  Il modello contiene riferimenti ModelBus a un altro modello.  È possibile utilizzare ModelBus per aprire il modello a cui si fa riferimento e per accedere a un determinato elemento.  Per ulteriori informazioni, vedere [Utilizzo di ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 In uno scenario meno comune, potrebbe essere necessario aprire un file modello per il quale si dispone di un nome file e che potrebbe non essere disponibile corrente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto.  In questo caso, è possibile aprire il file utilizzando la tecnica descritta in [Procedura: aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## Generazione di più file da un modello  
 Se si desidera generare molti file, ad esempio generare un file separato per ogni elemento in un modello, esistono molti approcci possibili.  Per impostazione predefinita, solo un file viene scritto da ciascun file modello.  
  
### Suddividere un file lunghi  
 In questo metodo, si utilizza un modello per generare un file, separati da un delimitatore.  Quindi è suddiviso il file nelle relative parti.  Esistono due modelli, uno per generare il file singolo e l'altro per quella.  
  
 **LoopTemplate.t4** genera un singolo file lunghi.  Si noti che l'estensione di file è “.t4„, poiché non deve essere elaborata direttamente quando si fa clic su **Trasformazione di tutti i modelli**.  Questo modello accetta un parametro, che specifica la stringa di delimitazione che separa i segmenti:  
  
```  
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
<#@ parameter name="delimiter" type="System.String" #>  
<#@ output extension=".txt" #>  
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>  
<#  
  // Create a file segment for each element:  
  foreach (ExampleElement element in this.ExampleModel.Elements)   
  {   
    // First item is the delimiter:  
#>  
<#= string.Format(delimiter, element.Id) #>  
  
   Element: <#= element.Name #>  
<#  
   // Here you generate more content derived from the element.  
  }  
#>  
  
```  
  
 `LoopSplitter.tt` richiama  `LoopTemplate.t4`quindi divide il file risultante nei relativi segmenti.  Si noti che questo modello non deve essere un modello di modellizzazione, poiché non legge il modello.  
  
```  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>  
<#@ import namespace="System.Runtime.Remoting.Messaging" #>  
<#@ import namespace="System.IO" #>  
  
<#  
  // Get the local path:  
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");  
  string dir = Path.GetDirectoryName(itemTemplatePath);  
  
  // Get the template for generating each file:  
  string loopTemplate = File.ReadAllText(itemTemplatePath);  
  
  Engine engine = new Engine();  
  
  // Pass parameter to new template:  
  string delimiterGuid = Guid.NewGuid().ToString();  
  string delimiter = "::::" + delimiterGuid + ":::";  
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");   
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);  
  
  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);  
  
  foreach (string nameAndFile in separateFiles)   
  {   
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;  
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);  
     if (parts.Length < 2) continue;  
#>  
 Generate: [<#= dir #>] [<#= parts[0] #>]  
<#  
     // Generate a file from this item:  
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);    
  }  
#>  
  
```