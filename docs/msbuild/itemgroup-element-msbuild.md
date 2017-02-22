---
title: "Elemento ItemGroup (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup (elemento) [MSBuild]"
  - "Elemento <ItemGroup> [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento ItemGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene un insieme di elementi [Item](../msbuild/item-element-msbuild.md) definiti dall'utente.  Ogni elemento utilizzato in un progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve essere specificato come elemento figlio di un elemento `ItemGroup`.  
  
## Sintassi  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo.  Condizione da valutare.  Per ulteriori informazioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione.  In un elemento `ItemGroup` possono essere presenti zero o più elementi `Item`.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[Destinazione](../msbuild/target-element-msbuild.md)|A partire da .NET Framework 3.5, l'elemento `ItemGroup` può essere visualizzato all'interno di un elemento `Target`.  Per ulteriori informazioni, vedere [Targets](../msbuild/msbuild-targets.md).|  
  
## Note  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrata la dichiarazione delle raccolte di elementi `Res` e `CodeFiles` definite dall'utente all'interno di un elemento `ItemGroup`.  Ogni elemento della raccolta `Res` contiene un elemento [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) figlio definito dell'utente.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## Vedere anche  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)   
 [Common MSBuild Project Items](../msbuild/common-msbuild-project-items.md)