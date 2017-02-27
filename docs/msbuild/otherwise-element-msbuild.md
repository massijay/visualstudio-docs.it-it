---
title: "Otherwise Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Otherwise"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Otherwise> Element [MSBuild]"
  - "Otherwise Element [MSBuild]"
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Otherwise Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica il blocco di codice da eseguire soltanto se le condizioni di tutti gli elementi `When` restituiscono `false`.  
  
## Sintassi  
  
```  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento facoltativo.<br /><br /> Valuta gli elementi figlio per selezionare una sezione di codice da eseguire.  In un elemento `Otherwise` possono essere presenti zero o più elementi `Choose`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un insieme di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente.  In un elemento `Otherwise` possono essere presenti zero o più elementi `ItemGroup`.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento facoltativo.<br /><br /> Contiene un insieme di elementi [Property](../msbuild/property-element-msbuild.md) definiti dall'utente.  In un elemento `Otherwise` possono essere presenti zero o più elementi `PropertyGroup`.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Valuta gli elementi figlio per selezionare una sezione di codice da eseguire.|  
  
## Note  
 In un elemento `Choose` può essere presente un unico elemento `Otherwise` ed è necessario che compaia per ultimo.  
  
 Gli elementi `Choose`, `When` e `Otherwise` vengono utilizzati insieme per consentire di selezionare una sezione di codice da eseguire tra diverse alternative.  Per ulteriori informazioni, vedere [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md).  
  
## Esempio  
 Nel progetto riportato di seguito l'elemento `Choose` viene utilizzato per selezionare l'insieme di valori delle proprietà da impostare negli elementi `When`.  Se gli attributi `Condition` di entrambi gli elementi `When` restituiscono `false`, i valori delle proprietà dell'elemento `Otherwise` vengono impostati.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
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
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
        </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  
  
## Vedere anche  
 [Conditional Constructs](../msbuild/msbuild-conditional-constructs.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)