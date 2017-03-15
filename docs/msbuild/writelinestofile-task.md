---
title: "WriteLinesToFile Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WriteLinesToFile task [MSBuild]"
  - "MSBuild, WriteLinesToFile task"
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# WriteLinesToFile Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Scrive i percorsi degli elementi specificati nel file di testo specificato.  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `WriteLinestoFile`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`File`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file in cui scrivere gli elementi.|  
|`Lines`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli elementi da scrivere nel file.|  
|`Overwrite`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, l'eventuale contenuto del file viene sovrascritto.|  
|`Encoding`|Parametro `String` facoltativo.<br /><br /> Consente di selezionare la codifica dei caratteri, ad esempio, "Unicode".  Vedere anche <xref:System.Text.Encoding>.|  
  
## Note  
 Se `Overwrite` è `true`, viene creato un nuovo file nel quale viene scritto il contenuto, quindi il file viene chiuso.  Se il file di destinazione è già esistente, viene sovrascritto.  Se `Overwrite` è `false`, il contenuto viene accodato al file e viene creato il file di destinazione, se non esiste già.  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `WriteLinesToFile` viene utilizzata per scrivere i percorsi degli elementi della raccolta `MyItems` nel file specificato dalla raccolta di elementi `MyTextFile`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)