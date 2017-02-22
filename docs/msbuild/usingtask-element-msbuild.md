---
title: "UsingTask Element (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#UsingTask"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UsingTask element [MSBuild]"
  - "<UsingTask> element [MSBuild]"
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
caps.latest.revision: 23
caps.handback.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UsingTask Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Associa l'attività a cui si fa riferimento in un elemento [Task](../msbuild/task-element-msbuild.md) all'assembly che contiene l'implementazione dell'attività.  
  
## Sintassi  
  
```  
<UsingTask TaskName="TaskName"  
    AssemblyName = "AssemblyName"   
    TaskFactory = "ClassName"  
    Condition="'String A'=='String B'" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`AssemblyName`|Sono obbligatori sia l'attributo `AssemblyName` che l'attributo `AssemblyFile`.<br /><br /> Nome dell'assembly da caricare.  L'attributo `AssemblyName` accetta assembly con nome sicuro, anche se non è obbligatorio un nome sicuro.  L'uso di questo attributo equivale a caricare un assembly usando il metodo <xref:System.Reflection.Assembly.Load%2A> in .NET.<br /><br /> Non è possibile usare questo attributo se viene usato l'attributo `AssemblyFile`.|  
|`AssemblyFile`|È obbligatorio l'attributo `AssemblyName` o l'attributo `AssemblyFile`.<br /><br /> Percorso del file dell'assembly.  Questo attributo accetta percorsi completi o percorsi relativi.  I percorsi relativi sono relativi alla directory del file di progetto o file di destinazioni in cui viene dichiarato l'elemento `UsingTask`.  L'uso di questo attributo equivale a caricare un assembly usando il metodo <xref:System.Reflection.Assembly.LoadFrom%2A> in .NET.<br /><br /> Non è possibile usare questo attributo se viene usato l'attributo `AssemblyName`.|  
|`TaskFactory`|Attributo facoltativo.<br /><br /> Specifica la classe nell'assembly responsabile della generazione di istanze del nome `Task` specificato.  L'utente può specificare anche un elemento figlio `TaskBody` che la factory delle attività riceve e usa per generare l'attività.  I contenuti dell'elemento `TaskBody` sono specifici per la factory delle attività.|  
|`TaskName`|Attributo obbligatorio.<br /><br /> Il nome dell'attività a cui fare riferimento da un assembly.  In caso di ambiguità, questo attributo deve specificare sempre gli spazi dei nomi completi.  In caso di ambiguità, MSBuild sceglie una corrispondenza arbitraria, con potenziali risultati imprevisti.|  
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare.  Per altre informazioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Il set di parametri visualizzati nell'attività generata dall'elemento `TaskFactory` specificato.|  
|[Attività](../msbuild/task-element-msbuild.md)|I dati che vengono passati all'elemento `TaskFactory` per generare un'istanza dell'attività.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Note  
 È possibile fare riferimento alle variabili di ambiente, alle proprietà della riga di comando e alle proprietà a livello di progetto in qualsiasi punto nell'elemento `UsingTask` se viene visualizzato nel file di progetto in modo esplicito o tramite un file di progetto importato.  Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md).  
  
> [!NOTE]
>  Le proprietà a livello di progetto non hanno alcun effetto se l'elemento `UsingTask` proviene da uno dei file con estensione tasks registrati a livello globale con il motore MSBuild.  Le proprietà a livello di progetto non sono globali per MSBuild.  
  
 In MSBuild 4.0 è possibile caricare gli elementi UsingTask dai file con estensione overridetask.  
  
## Esempio  
 L'esempio seguente illustra come usare l'elemento `UsingTask` con un attributo `AssemblyName`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
              ...  
</ParameterGroup>  
       <TaskBody>  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Esempio  
 L'esempio seguente illustra come usare l'elemento `UsingTask` con un attributo `AssemblyFile`.  
  
```  
<UsingTask TaskName="Email"  
              AssemblyFile="c:\myTasks\myTask.dll" />  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)