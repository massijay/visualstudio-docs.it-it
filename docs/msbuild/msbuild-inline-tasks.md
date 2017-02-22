---
title: "MSBuild Inline Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, tasks"
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Inline Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In genere le attività MSBuild vengono create compilando una classe che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>.  Per ulteriori informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md).  
  
 A partire dalla versione 4 di .NET Framework è possibile creare attività inline nel file di progetto.  Non è necessario creare un assembly a parte per ospitare l'attività.  Grazie a questa possibilità, tenere traccia del codice sorgente e distribuire l'attività risulta più semplice.  Il codice sorgente è integrato nello script.  
  
## Struttura di un'attività inline  
 Un'attività inline è contenuta in un elemento [UsingTask](../msbuild/usingtask-element-msbuild.md).  In genere l'attività inline e l'elemento `UsingTask` che la contiene sono inclusi in un file targets e vengono importati in altri file di progetto secondo le esigenze.  Ecco un'attività inline di base.  Notare che non esegue alcuna operazione.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task does nothing. -->  
  <UsingTask  
    TaskName="DoNothing"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="" />  
      <Using Namespace="" />  
      <Code Type="Fragment" Language="cs">  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 L'elemento `UsingTask` nell'esempio presenta tre attributi che descrivono l'attività e la factory delle attività inline che la compila.  
  
-   L'attributo `TaskName` denomina l'attività, in questo caso assegnando il nome `DoNothing`.  
  
-   L'attributo `TaskFactory` denomina la classe che implementa la factory delle attività inline.  
  
-   L'attributo `AssemblyFile` fornisce il percorso della factory delle attività inline.  In alternativa, l'attributo `AssemblyName` può essere utilizzato per specificare il nome completo della classe della factory delle attività inline, che in genere si trova nella Global Assembly Cache \(GAC\).  
  
 Gli elementi restanti dell'attività `DoNothing` sono vuoti e sono forniti per illustrare l'ordine e la struttura di un'attività inline.  Un esempio più completo viene presentato più avanti in questo argomento.  
  
-   L'elemento `ParameterGroup` è facoltativo.  Quando specificato, dichiara i parametri dell'attività.  Per ulteriori informazioni sui parametri di input e di output, vedere la sezione "Parametri di input e di output" più avanti in questo argomento.  
  
-   L'elemento `Task` descrive e contiene il codice sorgente dell'attività.  
  
-   L'elemento `Reference` specifica i riferimenti agli assembly .NET che si utilizzano nel codice.  Ciò equivale all'aggiunta di un riferimento a un progetto in Visual Studio.  L'attributo `Include` specifica il percorso dell'assembly a cui si fa riferimento.  
  
-   L'elemento `Using` elenca gli spazi dei nomi a cui si desidera accedere.  Tale elemento assomiglia all'istruzione `Using` in Visual C\#.  L'attributo `Namespace` specifica lo spazio dei nomi da includere.  
  
 Gli elementi `Reference` e `Using` sono indipendenti dal linguaggio.  Le attività inline possono essere scritte in uno dei linguaggi .NET CodeDOM supportati, ad esempio Visual Basic, Visual C\#.  
  
> [!NOTE]
>  Gli elementi contenuti nell'elemento `Task` sono specifici della factory delle attività, in questo caso della factory delle attività del codice.  
  
### Elemento Code  
 L'ultimo elemento figlio dell'elemento `Task` è l'elemento `Code`.  L'elemento `Code` contiene o individua il codice di cui si desidera la compilazione in un'attività.  Il contenuto che si inserisce nell'elemento `Code` dipende da come si desidera scrivere l'attività.  
  
 L'attributo `Language` specifica il linguaggio utilizzato per scrivere il codice.  I valori accettabili sono `cs` per C\#, `vb` per Visual Basic.  
  
 L'attributo `Type` specifica il tipo di codice contenuto nell'elemento `Code`.  
  
-   Se il valore di `Type` è `Class`, l'elemento `Code` contiene codice di una classe che deriva dall'interfaccia <xref:Microsoft.Build.Framework.ITask>.  
  
-   Se il valore di `Type` è `Method`, il codice definisce un override del metodo `Execute` dell'interfaccia <xref:Microsoft.Build.Framework.ITask>.  
  
-   Se il valore di `Type` è `Fragment`, il codice definisce il contenuto del metodo `Execute`, ma non la firma o l'istruzione `return`.  
  
 Di solito il codice in sé si trova tra un marcatore `<![CDATA[` e un marcatore `]]>`.  Poiché il codice è in una sezione CDATA, non è necessario preoccuparsi di eseguire l'escape di caratteri riservati, ad esempio "\<" o "\>".  
  
 In alternativa, è possibile utilizzare l'attributo `Source` dell'elemento `Code` per specificare il percorso di un file che contiene il codice dell'attività.  Il tipo del codice nel file di origine deve corrispondere a quello specificato dall'attributo `Type`.  Se è presente l'attributo `Source`, il valore predefinito di `Type` è `Class`.  Se `Source` non è presente, il valore predefinito è `Fragment`.  
  
> [!NOTE]
>  Quando si definisce la classe dell'attività nel file di origine, il nome della classe deve corrispondere all'attributo `TaskName` dell'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md) corrispondente.  
  
## Hello World  
 Ecco un'attività inline più completa.  L'attività HelloWorld consente di visualizzare "Hello, world\!" nel dispositivo di registrazione degli errori predefinito, che in genere è rappresentato dalla console di sistema o dalla finestra **Output** di Visual Studio.  L'elemento `Reference` nell'esempio è incluso solo per completezza.  
  
```  
<Project ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- This simple inline task displays "Hello, world!" -->  
  <UsingTask  
    TaskName="HelloWorld"  
    TaskFactory="CodeTaskFactory"  
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
    <ParameterGroup />  
    <Task>  
      <Reference Include="System.Xml.dll"/>  
      <Using Namespace="System"/>  
      <Using Namespace="System.IO"/>  
      <Code Type="Fragment" Language="cs">  
<![CDATA[  
// Display "Hello, world!"  
Log.LogError("Hello, world!");  
]]>  
      </Code>  
    </Task>  
  </UsingTask>  
</Project>  
```  
  
 È possibile salvare l'attività HelloWorld in un file denominato HelloWorld.targets e quindi richiamarlo da un progetto come illustrato di seguito.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <Import Project="HelloWorld.targets" />  
  <Target Name="Hello">  
    <HelloWorld />  
  </Target>  
</Project>  
```  
  
## Parametri di input e di output  
 I parametri delle attività inline sono elementi figlio di un elemento `ParameterGroup`.  Ogni parametro assume il nome dell'elemento che lo definisce.  Il codice seguente definisce il parametro `Text`.  
  
```  
<ParameterGroup>  
    <Text />  
</ParameterGroup>  
```  
  
 È possibile che i parametri presentino uno o più di questi attributi:  
  
-   `Required` è un attributo facoltativo che è `false` per impostazione predefinita.  Se `true`, il parametro è obbligatorio e occorre fornirgli un valore prima di chiamare l'attività.  
  
-   `ParameterType` è un attributo facoltativo che è `System.String` per impostazione predefinita.  Può essere impostato su qualsiasi tipo completo che è un elemento o un valore che può essere convertito da e in una stringa tramite System.Convert.ChangeType. In altre parole, può essere impostato su qualsiasi tipo che può essere passato da e a un'attività esterna.  
  
-   `Output` è un attributo facoltativo che è `false` per impostazione predefinita.  Se `true`, occorre fornire un valore al parametro prima che il metodo Execute restituisca un valore.  
  
 Di seguito è riportato un esempio:  
  
```  
<ParameterGroup>  
    <Expression Required="true" />  
      <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
    <Tally ParameterType="System.Int32" Output="true" />  
</ParameterGroup>  
```  
  
 definisce questi tre parametri:  
  
-   `Expression` è un parametro di input obbligatorio di tipo System.String.  
  
-   `Files` è un parametro di input di elenco di elementi obbligatorio.  
  
-   `Tally` è un parametro di output di tipo System.Int32.  
  
 Se l'attributo `Type` dell'elemento `Code` è `Fragment` o `Method`, le proprietà vengono create automaticamente per ogni parametro.  In caso contrario, è necessario dichiarare le proprietà in modo esplicito nel codice sorgente dell'attività. Inoltre, tali proprietà devono corrispondere esattamente alle proprie definizioni di parametro.  
  
## Esempio  
 L'attività inline seguente sostituisce ogni occorrenza di un token nel file specificato con il valore specificato.  
  
```  
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="12.0">  
  
  <UsingTask TaskName="TokenReplace" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v12.0.dll">  
    <ParameterGroup>  
      <Path ParameterType="System.String" Required="true" />  
      <Token ParameterType="System.String" Required="true" />  
      <Replacement ParameterType="System.String" Required="true" />  
    </ParameterGroup>  
    <Task>  
      <Code Type="Fragment" Language="cs"><![CDATA[  
string content = File.ReadAllText(Path);  
content = content.Replace(Token, Replacement);  
File.WriteAllText(Path, content);  
  
]]></Code>  
    </Task>  
  </UsingTask>  
  
  <Target Name='Demo' >  
    <TokenReplace Path="C:\Project\Target.config" Token="$MyToken$" Replacement="MyValue"/>  
  </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Walkthrough: Creating an Inline Task](../Topic/Walkthrough:%20Creating%20an%20Inline%20Task.md)