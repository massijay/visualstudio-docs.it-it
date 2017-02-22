---
title: "CallTarget Task | Microsoft Docs"
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
  - "CallTarget task [MSBuild]"
  - "MSBuild, CallTarget task"
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CallTarget Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Richiama le destinazioni specificate all'interno del file di progetto.  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `CallTarget`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Parametro di output `Boolean` facoltativo.<br /><br /> Se `true`, il motore [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] viene chiamato una volta per ciascuna destinazione.  Se `false`, il modulo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] viene chiamato una volta per compilare tutte le destinazioni.  Il valore predefinito è `false`.|  
|`TargetOutputs`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli output di tutte le destinazioni compilate.|  
|`Targets`|Parametro `String[]` facoltativo.<br /><br /> Specifica la destinazione o le destinazioni da compilare.|  
|`UseResultsCache`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene restituito il risultato memorizzato nella cache, se presente.<br /><br /> **Nota** Quando viene eseguita un'attività MSBuild, il relativo output viene memorizzato nella cache in un ambito \(ProjectFileName, GlobalProperties\)\[TargetNames\] come elenco di elementi di compilazione.|  
  
## Note  
 Se una destinazione specificata in `Targets` ha esito negativo e `RunEachTargetSeparately` è `true`, l'attività continua a compilare le destinazioni rimanenti.  
  
 Se si desidera compilare le destinazioni predefinite, utilizzare [Attività MSBuild](../msbuild/msbuild-task.md) e impostare il parametro `Projects` sullo stesso valore di `$(MSBuildProjectFile)`.  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito `TargetA` viene chiamato dall'interno di `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)