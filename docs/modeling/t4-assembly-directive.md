---
title: "T4 Assembly Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 4
---
# T4 Assembly Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In un modello di testo della fase di progettazione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la direttiva `assembly` carica un assembly in modo che il codice del modello possa utilizzarne i tipi.  L'effetto è simile all'aggiunta di un riferimento all'assembly in un progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Per cenni preliminari sulla scrittura dei modelli di testo, vedere [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  La direttiva `assembly` in un modello di testo \(pre\-elaborato\) della fase di esecuzione non è necessaria.  Aggiungere invece gli assembly necessari ai **Riferimenti** del progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Utilizzo della direttiva Assembly  
 La sintassi della direttiva è la seguente:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 Il nome dell'assembly deve essere uno dei seguenti:  
  
-   Il nome sicuro dell'assembly nella GAC, quale `System.Xml.dll`.  È inoltre possibile utilizzare la forma estesa, quale `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`.  Per ulteriori informazioni, vedere <xref:System.Reflection.AssemblyName>.  
  
-   Il percorso assoluto dell'assembly  
  
 È possibile utilizzare anche la sintassi `$(variableName)` per fare riferimento alle variabili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], quali `$(SolutionDir)` e `%VariableName%` per fare riferimento alle variabili di ambiente.  Ad esempio:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 La direttiva dell'assembly non ha alcun effetto in un modello di testo pre\-elaborato.  Al contrario, si consiglia di includere i riferimenti necessari nella sezione **Riferimenti** del progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Assembly standard  
 Gli assembly seguenti vengono caricati automaticamente, in modo che non sia necessario scrivere per essi direttive dell'assembly:  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 Se si utilizza una direttiva personalizzata, il processore di direttiva potrebbe caricare assembly aggiuntivi.  Ad esempio, se si scrivono modelli per un linguaggio specifico di dominio \(DSL\), non è necessario scrivere direttive dell'assembly per gli assembly seguenti:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   Assembly contenente il modello DSL.  
  
##  <a name="msbuild"></a> Utilizzo delle proprietà del progetto in MSBuild e Visual Studio  
 Le macro di Visual Studio, ad esempio $\(SolutionDir\), non funzionano in MSBuild.  Se si desidera trasformare i modelli nel computer di compilazione, è necessario utilizzare le proprietà del progetto.  
  
 Modificare il file con estensione csproj o vbproj per definire una proprietà del progetto.  In questo esempio viene definita una proprietà denominata `myLibFolder`:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 È ora possibile utilizzare la proprietà del progetto nei modelli di testo, che si convertono correttamente in Visual Studio e in MSBuild:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## Vedere anche  
 [T4 Include Directive](../modeling/t4-include-directive.md)