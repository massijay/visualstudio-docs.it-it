---
title: "Parameter Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Parameter element [MSBuild]"
  - "<Parameter> element [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Parameter Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene informazioni su un parametro specifico per un'attività generata da un oggetto `UsingTask` `TaskFactory`. Il nome dell'elemento è il nome del parametro. Per ulteriori informazioni, vedere [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Sintassi  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`ParameterType`|Attributo facoltativo.<br /><br /> Tipo .NET del parametro, ad esempio, "System.String".|  
|`Output`|Attributo booleano facoltativo.<br /><br /> Se `true`, questo parametro è un parametro di output per l'attività.  Per impostazione predefinita, il valore è `false`.|  
|`Required`|Attributo booleano facoltativo.<br /><br /> Se `true`, questo parametro è un parametro obbligatorio per l'attività.  Per impostazione predefinita, il valore è `false`.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene un elenco facoltativo dei parametri che saranno presenti nell'attività generata da un oggetto `UsingTask` `TaskFactory`.|  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'elemento `Parameter`:  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)