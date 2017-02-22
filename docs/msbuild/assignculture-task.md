---
title: "AssignCulture Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AssignCulture task"
  - "AssignCulture task [MSBuild]"
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AssignCulture Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa attività accetta un elenco di elementi che possono contenere una stringa di identificazione delle impostazioni cultura .NET valida come parte del nome di file e genera elementi con un metadato denominato `Culture` contenente l'identificatore delle impostazioni cultura corrispondente.  Ad esempio, poiché il nome di file Form1.fr\-fr.resx contiene l'identificatore delle impostazioni cultura incorporato "fr\-fr", verrà generato un elemento con lo stesso nome di file in cui il valore del metadato `Culture` sarà `fr-fr`.  L'attività genera inoltre un elenco di nomi di file dai quali l'identificatore delle impostazioni cultura è stato rimosso.  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `AssignCulture`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssignedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di elementi ricevuti nel parametro `Files`. A ciascun elemento è stato aggiunto un metadato `Culture`.<br /><br /> Se l'elemento proveniente dal parametro `Files` contiene già un metadato `Culture`, viene utilizzato il metadato originale.<br /><br /> L'attività assegna una voce di metadati `Culture` solo se il nome file contiene un identificatore delle impostazioni cultura valido.  L'identificatore delle impostazioni cultura deve essere compreso tra gli ultimi due punti del nome di file.|  
|`AssignedFilesWithCulture`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene il sottoinsieme degli elementi del parametro `AssignedFiles` che presentano un metadato `Culture`.|  
|`AssignedFilesWithNoCulture`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene il sottoinsieme degli elementi del parametro `AssignedFiles` che non presentano un metadato `Culture`.|  
|`CultureNeutralAssignedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene lo stesso elenco di elementi generato nel parametro `AssignedFiles`, con la differenza che l'identificatore delle impostazioni cultura è stato rimosso dal nome di file.<br /><br /> Le impostazioni cultura vengono rimosse dal nome di file soltanto se si tratta di un identificatore delle impostazioni cultura valido.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco di file con i nomi di impostazioni cultura incorporati a cui assegnare determinate impostazioni cultura.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `AssignCulture` viene eseguita con la raccolta di elementi `ResourceFiles`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 Nella tabella riportata di seguito viene descritto il valore degli elementi di output dopo l'esecuzione dell'attività.  I metadati degli elementi vengono visualizzati tra parentesi dopo l'elemento.  
  
|Raccolta di elementi|Contenuto|  
|--------------------------|---------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` \(nessun metadato aggiuntivo\)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` \(nessun metadato aggiuntivo\)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (`nessun metadato aggiuntivo\)|  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)