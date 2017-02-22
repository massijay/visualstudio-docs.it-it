---
title: "CreateProperty Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CreateProperty task [MSBuild]"
  - "MSBuild, CreateProperty task"
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CreateProperty Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inserisce gli elementi passati nelle proprietà.   Questa attività consente di copiare tali valori da una proprietà o stringa a un'altra.  
  
## Attributi  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `CreateProperty`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Value`|Parametro di output `String` facoltativo.<br /><br /> Specifica il valore da copiare nella nuova proprietà.|  
|`ValueSetByTask`|Parametro di output `String` facoltativo.<br /><br /> Contiene lo stesso valore del parametro `Value`.  Utilizzare questo parametro solo per evitare che la proprietà di output venga impostata da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nei casi in cui la destinazione di inclusione viene ignorata perché gli output sono aggiornati.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `CreateProperty` viene utilizzata per creare la proprietà `NewFile` utilizzando la combinazione dei valori delle proprietà `SourceFilename` e `SourceFileExtension`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 Al termine dell'esecuzione del progetto, il valore della proprietà `NewFile` è `Module1.vb`.  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)