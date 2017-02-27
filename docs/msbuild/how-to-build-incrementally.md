---
title: "How to: Build Incrementally | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, incremental builds"
  - "incremental builds"
  - "MSBuild, building incrementally"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Build Incrementally
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si compila un progetto di grandi dimensioni, è importante che i componenti creati in precedenza che risultano ancora aggiornati non vengano ricompilati.  Se tutte le destinazioni venissero compilate ogni volta, il completamento delle singole compilazioni richiederebbe un tempo eccessivo.  Per attivare le compilazioni incrementali, in cui vengono ricompilate solo le destinazioni non compilate in precedenza o le destinazioni non aggiornate, [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) può confrontare i timestamp dei file di input con i timestamp dei file di output e stabilire se ignorare, compilare o ricompilare parzialmente una destinazione.  È tuttavia necessario che il mapping tra input e output sia di tipo uno\-a\-uno.  Per consentire alle destinazioni di identificare questo mapping diretto, è possibile utilizzare le trasformazioni.  Per ulteriori informazioni sulle trasformazioni, vedere [Transforms](../msbuild/msbuild-transforms.md).  
  
## Specifica di input e output  
 Una destinazione può essere compilata in modo incrementale se input e output sono specificati nel file di progetto.  
  
#### Per specificare input e output per una destinazione  
  
-   Utilizzare gli attributi `Inputs` e `Outputs` dell'elemento `Target`.  Ad esempio:  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] può confrontare i timestamp dei file di input con i timestamp dei file di output e stabilire se ignorare, compilare o ricompilare parzialmente una destinazione.  Nell'esempio riportato di seguito, se uno qualsiasi dei file dell'elenco di elementi `@(CSFile)` è più recente del file hello.exe, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] eseguirà la destinazione. In caso contrario, questa verrà ignorata.  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Quando in una destinazione vengono specificati input e output, ogni output potrà essere mappato a un solo input oppure non sarà possibile eseguire il mapping diretto tra output e input.  Nell'attività [Csc Task](../msbuild/csc-task.md) precedente, ad esempio, non è possibile eseguire il mapping dell'output hello.exe ad alcun input singolo, ma l'output dipende da tutti gli input.  
  
> [!NOTE]
>  Le destinazioni in cui non si verifica il mapping diretto tra input e output verranno sempre compilate con maggiore frequenza rispetto a quelle in cui si esegue il mapping di ogni output a un solo input poiché [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non è in grado di stabilire quale output debba essere ricompilato in caso di modifica di alcuni input.  
  
 Le attività in cui è possibile identificare un mapping diretto tra output e input, ad esempio l'attività [LC Task](../msbuild/lc-task.md), sono più adatte alla compilazione incrementale, diversamente da attività quali `Csc` e [Vbc](../msbuild/vbc-task.md), che producono un assembly di output da numerosi input.  
  
## Esempio  
 Nell'esempio riportato di seguito viene utilizzato un progetto che compila file della Guida per un ipotetico sistema di Guida.  Il progetto prevede la conversione dei file txt di origine in file content intermedi, che vengono quindi combinati ai file di metadati XML per produrre il file finale con estensione help utilizzato dal sistema di Guida.  Nel progetto vengono utilizzate le seguenti attività ipotetiche:  
  
-   `GenerateContentFiles`: converte i file txt in file content.  
  
-   `BuildHelp`: combina i file content e i file di metadati XML per compilare il file finale con estensione help.  
  
 Il progetto utilizza le trasformazioni per creare mapping uno\-a\-uno tra input e output nell'attività `GenerateContentFiles`.  Per ulteriori informazioni, vedere [Transforms](../msbuild/msbuild-transforms.md).  L'elemento `Output` viene inoltre impostato in modo da utilizzare automaticamente gli output dell'attività `GenerateContentFiles` come input per l'attività `BuildHelp`.  
  
 Questo file di progetto contiene entrambe le destinazioni `Convert` e `Build`.  Le attività `GenerateContentFiles` e `BuildHelp` vengono posizionate, rispettivamente, nelle destinazioni `Convert` e `Build`, in modo da consentire la compilazione incrementale delle singole destinazioni.  Se si utilizza l'elemento `Output`, gli output dell'attività `GenerateContentFiles` vengono posizionati nell'elenco di elementi `ContentFile`, in cui possono essere utilizzati come input per l'attività `BuildHelp`.  Questa applicazione dell'elemento `Output` consente di utilizzare automaticamente gli output di un'attività come input per un'altra attività, senza dover elencare manualmente i singoli elementi o elenchi di elementi in ogni attività.  
  
> [!NOTE]
>  Sebbene la destinazione `GenerateContentFiles` possa essere compilata in modo incrementale, tutti gli output di tale destinazione sono sempre necessari come input per la destinazione `BuildHelp`.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fornisce automaticamente tutti gli output di una destinazione come input per un'altra destinazione quando si utilizza l'elemento `Output`.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
    </ItemGroup>  
  
    <Target Name = "Convert"  
        Inputs="@(TXTFile)"  
        Outputs="@(TXTFile->'%(Filename).content')">  
  
        <GenerateContentFiles  
            Sources = "@(TXTFile)">  
            <Output TaskParameter = "OutputContentFiles"  
                ItemName = "ContentFiles"/>  
        </GenerateContentFiles>  
    </Target>  
  
    <Target Name = "Build" DependsOnTargets = "Convert"  
        Inputs="@(ContentFiles);@(XMLFiles)"  
        Outputs="$(MSBuildProjectName).help">  
  
        <BuildHelp  
            ContentFiles = "@(ContentFiles)"  
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Targets](../msbuild/msbuild-targets.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Transforms](../msbuild/msbuild-transforms.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Vbc Task](../msbuild/vbc-task.md)