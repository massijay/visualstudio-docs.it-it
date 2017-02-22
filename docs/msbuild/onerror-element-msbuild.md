---
title: "OnError Element (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#OnError"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "OnError Element [MSBuild]"
  - "<OnError Element [MSBuild]"
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# OnError Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina l'esecuzione di una o più destinazioni se l'attributo `ContinueOnError` è impostato su `false` per un'attività non riuscita.  
  
## Sintassi  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare.  Per ulteriori informazioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Attributo obbligatorio.<br /><br /> Destinazioni da eseguire se un'attività ha esito negativo.  Se sono specificate più destinazioni, separarle con punti e virgola.  Le diverse destinazioni vengono eseguite nell'ordine specificato.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Destinazione](../msbuild/target-element-msbuild.md)|Elemento contenitore per le attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Note  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] esegue l'elemento `OnError` se una delle attività dell'elemento `Target` non riesce con l'attributo `ContinueOnError` a `ErrorAndStop` o a `false`\).  Se l'attività ha esito negativo, vengono eseguite le destinazioni specificate nell'attributo `ExecuteTargets`.  Se nella destinazione sono presenti più elementi `OnError`, gli elementi `OnError` vengono eseguiti in sequenza quando l'attività ha esito negativo.  
  
 Per informazioni sull'attributo `ContinueOnError`, vedere [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md).  Per informazioni sulle destinazioni, vedere [Targets](../msbuild/msbuild-targets.md).  
  
## Esempio  
 Nell'esempio di codice riportato di seguito vengono eseguite le attività `TaskOne` e `TaskTwo`.  Se `TaskOne` ha esito negativo, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] valuta l'elemento `OnError` ed esegue la destinazione `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## Vedere anche  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)