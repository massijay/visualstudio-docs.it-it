---
title: "How to: Select the Files to Build | Microsoft Docs"
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
  - "MSBuild, wildcards"
  - "MSBuild, including files"
  - "Include attribute [MSBuild]"
ms.assetid: f5ff182f-7b3a-46fb-9335-37df54cfb8eb
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Select the Files to Build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si compila un progetto che contiene numerosi file, è possibile elencarli separatamente nel file di progetto oppure utilizzare caratteri jolly per includerli tutti in una directory o in un insieme annidato di directory.  
  
## Definizione degli input  
 Gli elementi rappresentano gli input per una compilazione.  Per ulteriori informazioni sugli elementi, vedere [Items](../msbuild/msbuild-items.md).  
  
 Per includere i file per una compilazione, è necessario inserirli in un elenco di elementi nel file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  È possibile aggiungere più file agli elenchi di elementi includendoli singolarmente oppure in blocco utilizzando i caratteri jolly.  
  
#### Per dichiarare gli elementi individualmente  
  
-   Utilizzare attributi `Include` simili a quelli riportati di seguito:  
  
     `<CSFile Include="form1.cs"/>`  
  
     \- oppure \-  
  
     `<VBFile Include="form1.vb"/>`  
  
    > [!NOTE]
    >  Se gli elementi in una raccolta di elementi non si trovano nella stessa directory del file di progetto, è necessario specificare il percorso completo o relativo dell' elemento.  Ad esempio: `Include="..\..\form2.cs"`.  
  
#### Per dichiarare più elementi  
  
-   Utilizzare attributi `Include` simili a quelli riportati di seguito:  
  
     `<CSFile Include="form1.cs;form2.cs"/>`  
  
     \- oppure \-  
  
     `<VBFile Include="form1.vb;form2.vb"/>`  
  
## Specifica degli input tramite caratteri jolly  
 I caratteri jolly possono inoltre essere utilizzati per includere in modo ricorsivo come input per una compilazione tutti i file, o solo alcuni di essi, presenti nelle sottodirectory.  Per ulteriori informazioni sui caratteri jolly, vedere [Items](../msbuild/msbuild-items.md).  
  
 Negli esempi riportati di seguito è illustrato un progetto che contiene file grafici nelle directory e sottodirectory indicate, con il file di progetto situato nella directory Project:  
  
 Project\\Images\\BestJpgs  
  
 Project\\Images\\ImgJpgs  
  
 Project\\Images\\ImgJpgs\\Img1  
  
#### Per includere tutti i file con estensione jpg presenti nella directory Images e nelle relative sottodirectory  
  
-   Utilizzare il seguente attributo `Include`:  
  
     `Include="Images\**\*.jpg"`  
  
#### Per includere tutti i file con estensione jpg il cui nome inizia con "img"  
  
-   Utilizzare il seguente attributo `Include`:  
  
     `Include="Images\**\img*.jpg"`  
  
#### Per includere tutti i file presenti nelle directory il cui nome termina in "jpgs"  
  
-   Utilizzare uno degli attributi `Include` seguenti:  
  
     `Include="Images\**\*jpgs\*.*"`  
  
     \- oppure \-  
  
     `Include="Images\**\*jpgs\*"`  
  
## Passaggio degli elementi a un'attività  
 In un file di progetto è possibile inserire la notazione @\(\) nelle attività per specificare come input per una compilazione un intero elenco di elementi.  Tale notazione può essere utilizzata sia che i file vengano elencati separatamente, sia che si utilizzino i caratteri jolly.  
  
#### Per utilizzare come input tutti i file Visual C\# o Visual Basic  
  
-   Utilizzare attributi `Include` simili a quelli riportati di seguito:  
  
     `<CSC Sources="@(CSFile)">...</CSC>`  
  
     \- oppure \-  
  
     `<VBC Sources="@(VBFile)">...</VBC>`  
  
> [!NOTE]
>  Per specificare gli input per una compilazione, è necessario utilizzare caratteri jolly con gli elementi. Non è consentito ricorrere all'attributo `Sources` in attività di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] quali [Csc](../msbuild/csc-task.md) o [Vbc](../msbuild/vbc-task.md).  L'esempio riportato di seguito non è considerato valido in un file di progetto:  
>   
>  `<CSC Sources="*.cs">...</CSC>`  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un progetto in cui tutti i file di input vengono inclusi separatamente.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Builtdir>built</Builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="Form1.cs"/>  
        <CSFile Include="AssemblyInfo.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene utilizzato un carattere jolly per includere tutti i file con estensione cs.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <builtdir>built</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs"/>  
  
        <Reference Include="System.dll"/>  
        <Reference Include="System.Data.dll"/>  
        <Reference Include="System.Drawing.dll"/>  
        <Reference Include="System.Windows.Forms.dll"/>  
        <Reference Include="System.XML.dll"/>  
    </ItemGroup>  
  
    <Target Name="PreBuild">  
        <Exec Command="if not exist $(builtdir) md $(builtdir)"/>  
    </Target>  
  
    <Target Name="Compile" DependsOnTargets="PreBuild">  
        <Csc Sources="@(CSFile)"  
            References="@(Reference)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).exe"  
            TargetType="exe" />  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [How to: Exclude Files from the Build](../msbuild/how-to-exclude-files-from-the-build.md)   
 [Items](../msbuild/msbuild-items.md)