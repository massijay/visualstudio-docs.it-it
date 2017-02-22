---
title: "ItemDefinitionGroup Element (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemDefinitionGroup Element [MSBuild]"
  - "<ItemDefinitionGroup> Element [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemDefinitionGroup Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento  `ItemDefinitionGroup` consente di definire un insieme di Definizioni di elementi che sono i valori dei metadati applicati a tutti gli elementi nel progetto per impostazione predefinita.  ItemDefinitionGroup ovvia al bisogno di utilizzare [CreateItem Task](../msbuild/createitem-task.md) e [CreateProperty Task](../msbuild/createproperty-task.md).  Per ulteriori informazioni, vedere [Item Definitions](../msbuild/item-definitions.md).  
  
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
|[Elemento](../msbuild/item-element-msbuild.md)|Definisce gli input per il processo di compilazione.  In un elemento `ItemDefinitionGroup` possono essere presenti zero o più elementi `Item`.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Esempio  
 Nell'esempio di codice seguente sono definiti due elementi di metadati, m ed n, in un ItemDefinitionGroup.  In questo esempio, i metadati predefiniti "m" sono applicati all'elemento "i" perché non sono definiti in modo esplicito dall'elemento "i".  I metadati predefiniti "n", invece, non sono applicati all'elemento "i" perché sono già definiti dall'elemento "i".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## Vedere anche  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)