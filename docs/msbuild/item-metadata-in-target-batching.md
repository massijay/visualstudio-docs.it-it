---
title: "Item Metadata in Target Batching | Microsoft Docs"
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
  - "MSBuild, target batching"
  - "target batching [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Item Metadata in Target Batching
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è possibile eseguire l'analisi delle dipendenze sugli input e sugli output di una destinazione di compilazione.  Se viene determinato che gli input o gli output della destinazione sono aggiornati, la destinazione viene ignorata e la compilazione procede.  Gli elementi `Target` utilizzano gli attributi `Inputs` e `Outputs` per specificare gli elementi da controllare durante l'analisi delle dipendenze.  
  
 Se una destinazione contiene un'attività che utilizza elementi suddivisi in batch come input o output, l'elemento `Target` della destinazione dovrebbe utilizzare la divisione in batch nei propri attributi `Inputs` o `Outputs` per consentire a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di ignorare i batch degli elementi già aggiornati.  
  
## Divisione in batch di destinazioni  
 L'esempio seguente contiene un elenco di elementi denominato `Res` che viene diviso in due batch in base ai metadati di elemento `Culture`.  Ciascuno dei batch viene passato nell'attività `AL`, la quale crea un assembly di output per ciascun batch.  Utilizzando la divisione in batch nell'attributo `Outputs` dell'elemento `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sarà in grado di determinare se ogni singolo batch è aggiornato prima di eseguire la destinazione.  Se non venisse utilizzata la divisione in batch della destinazione, entrambi i batch degli elementi verrebbero eseguiti dall'attività ogni volta che viene eseguita la destinazione.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## Vedere anche  
 [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md)   
 [Batching](../msbuild/msbuild-batching.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Item Metadata in Task Batching](../msbuild/item-metadata-in-task-batching.md)