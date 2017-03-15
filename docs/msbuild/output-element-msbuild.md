---
title: "Output Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Output"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Output> Element [MSBuild]"
  - "Output Element [MSBuild]"
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Output Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Archivia i valori di output dell'attività in elementi e proprietà.  
  
## Sintassi  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`TaskParameter`|Attributo obbligatorio.<br /><br /> Nome del parametro di output dell'attività.|  
|`PropertyName`|L'attributo `PropertyName` o `ItemName` è obbligatorio.<br /><br /> Proprietà che riceve il valore del parametro di output dell'attività.  Il progetto può quindi fare riferimento alla proprietà mediante la sintassi `$(`*PropertyName*`)`.  È possibile assegnare alla proprietà un nuovo nome o un nome già definito nel progetto.<br /><br /> Non è possibile utilizzare questo attributo se è già presente l'attributo `ItemName`.|  
|`ItemName`|L'attributo `PropertyName` o `ItemName` è obbligatorio.<br /><br /> Elemento che riceve il valore del parametro di output dell'attività.  Il progetto può quindi fare riferimento all'elemento mediante la sintassi `@(`*ItemName*`)`.  È possibile assegnare all'elemento un nuovo nome o un nome già definito nel progetto.<br /><br /> Non è possibile utilizzare questo attributo se è già presente l'attributo `PropertyName`.|  
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare.  Per ulteriori informazioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|Crea ed esegue un'istanza di un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrata l'esecuzione dell'attività `Csc` all'interno di un elemento `Target`.  Gli elementi e le proprietà passati all'attività vengono dichiarati al di fuori dell'ambito dell'esempio.  Il valore del parametro di output `OutputAssembly` viene archiviato nell'elemento `FinalAssemblyName` e quello del parametro di output `BuildSucceeded` viene archiviato nella proprietà `BuildWorked`.  Per ulteriori informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## Vedere anche  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)