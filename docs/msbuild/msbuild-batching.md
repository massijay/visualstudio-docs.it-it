---
title: "MSBuild Batching | Microsoft Docs"
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
  - "batching [MSBuild]"
  - "MSBuild, batching"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è possibile dividere gli elenchi di elementi in diverse categorie, o batch, in base ai metadati di elemento ed eseguire una destinazione o un'attività una sola volta per ciascun batch.  
  
## Divisione in batch di attività  
 La divisione in batch di un'attività consente di semplificare i file di progetto, offrendo un metodo per dividere gli elenchi di elementi in vari batch e passare separatamente ciascuno di questi batch a un'attività.  Ciò significa che un file di progetto necessita di una sola dichiarazione dell'attività e dei rispettivi attributi, anche se può essere eseguito più volte.  
  
 In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è necessario specificare che si desidera eseguire la divisione in batch con un'attività utilizzando la notazione %\(*NomeMetadatiElemento*\) in uno degli attributi dell'attività.  Nell'esempio seguente viene diviso l'elenco di elementi `Example` in batch in base al valore dei metadati di elemento `Color` e ogni batch viene passato separatamente all'attività `MyTask`.  
  
> [!NOTE]
>  Se non viene fatto riferimento all'elenco di elementi negli attributi dell'attività oppure se il nome dei metadati può risultare ambiguo, è possibile utilizzare la notazione %\(*InsiemeElementi.NomeMetadatiElemento*\) per specificare il nome completo del valore dei metadati di elemento da utilizzare per l'esecuzione in batch.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Per ulteriori esempi sulla divisione in batch, vedere [Item Metadata in Task Batching](../msbuild/item-metadata-in-task-batching.md).  
  
## Divisione in batch delle destinazioni  
 Prima di eseguire una destinazione, in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] viene controllato se gli input e gli output della destinazione sono aggiornati.  In caso affermativo, la destinazione verrà ignorata.  Se all'interno di una destinazione è presente un'attività che utilizza la divisione in batch, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve stabilire se gli input e gli output di ciascun batch di elementi risultano aggiornati.  In caso contrario, la destinazione verrà eseguita ogni volta che viene raggiunta.  
  
 Nell'esempio seguente viene illustrato un elemento `Target` che contiene un attributo `Outputs` con la notazione %\(*ItemMetaDataName*\).  In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] l'elenco di elementi `Example` viene suddiviso in batch in base ai metadati di elemento `Color` e vengono analizzati i timestamp dei file di output per ogni batch.  Se gli output di un batch non risultano aggiornati, la destinazione verrà eseguita.  In caso contrario, la destinazione verrà ignorata.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Per un altro esempio sulla divisione in batch delle destinazioni, vedere [Item Metadata in Target Batching](../msbuild/item-metadata-in-target-batching.md).  
  
## Funzioni delle proprietà che utilizzano i metadati  
 La suddivisione in batch può essere controllata da funzioni delle proprietà che includono metadati.  Di seguito è riportato un esempio:  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 utilizza <xref:System.IO.Path.Combine%2A> per combinare un percorso della cartella radice con un percorso dell'elemento Compile.  
  
 Le funzioni delle proprietà potrebbero non venire visualizzate nei valori dei metadati.  Di seguito è riportato un esempio:  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 non è consentito.  
  
 Per ulteriori informazioni sulle funzioni delle proprietà, vedere [Property Functions](../msbuild/property-functions.md).  
  
## Vedere anche  
 [ItemMetadata Element \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)