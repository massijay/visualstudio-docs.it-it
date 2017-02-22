---
title: "MSBuild Conditional Constructs | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Choose> Element [MSBuild]"
  - "Choose Element [MSBuild]"
  - "conditional constructs [MSBuild]"
  - "MSBuild, conditional constructs"
  - "<When> Element [MSBuild]"
  - "<Otherwise> Element [MSBuild]"
  - "Otherwise Element [MSBuild]"
  - "When Element [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Conditional Constructs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] offre un meccanismo per l'elaborazione either\/or mediante gli elementi [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) e [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## Utilizzo dell'elemento Choose  
 L'elemento `Choose` contiene una serie di elementi `When` con attributi `Condition` che vengono sottoposti a test dall'alto verso il basso, fino a quando un attributo non restituisce `true`.  Se più elementi `When` restituiscono `true`, viene utilizzato solo il primo.  Verrà restituito un elemento `Otherwise`, se presente, se nessuna condizione per un elemento `When` restituisce `true`.  
  
 Gli elementi `Choose` possono essere utilizzati come elementi figlio di `Project`, `When` e `Otherwise`.  Gli elementi `When` e `Otherwise` possono avere gli elementi figlio `ItemGroup`, `PropertyGroup` e `Choose`.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono utilizzati gli elementi `Choose` e `When` per l'elaborazione either\/or.  Le proprietà e gli elementi del progetto vengono impostati in base al valore della proprietà `Configuration`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='Debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
    </Choose>  
    <!-- Rest of Project -->  
</Project>  
```  
  
## Vedere anche  
 [Choose Element \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [When Element \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Otherwise Element \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)