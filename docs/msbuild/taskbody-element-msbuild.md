---
title: "TaskBody Element (MSBuild) | Microsoft Docs"
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
  - "TaskBody element [MSBuild]"
  - "<TaskBody> element [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# TaskBody Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene i dati che vengono passati a un oggetto `UsingTask` `TaskFactory`. Per ulteriori informazioni, vedere [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Sintassi  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Evaluate`|Attributo booleano facoltativo.<br /><br /> Se `true`, tramite MSBuild viene valutato qualsiasi elemento interno e vengono espansi elementi e proprietà prima che tale oggetto consenta il passaggio delle informazioni all'oggetto `TaskFactory` quando viene creata un'istanza dell'attività.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Dati|Il testo tra i tag `TaskBody` viene inviato alla lettera all'oggetto `TaskFactory`.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Consente di registrare le attività in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  In un progetto possono essere presenti zero o più elementi `UsingTask`.|  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'elemento `TaskBody` con un attributo `Evaluate`.  
  
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