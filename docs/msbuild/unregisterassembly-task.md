---
title: "Attività UnregisterAssembly | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
caps.latest.revision: 21
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 9f2973dcb28338d26b0c3372a95d166d1b2170a0
ms.lasthandoff: 02/22/2017

---
# <a name="unregisterassembly-task"></a>Attività UnregisterAssembly
Annulla la registrazione degli assembly specificati ai fini dell'interoperabilità COM. Esegue operazioni inverse rispetto all'[attività RegisterAssembly](../msbuild/registerassembly-task.md).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `UnregisterAssembly`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Assemblies`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica gli assembly di cui annullare la registrazione.|  
|`AssemblyListFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Contiene informazioni sullo stato tra l'attività `RegisterAssembly` e l'attività `UnregisterAssembly`. Questo impedisce all'attività di tentare l'annullamento della registrazione di un assembly che non è riuscita nell'attività `RegisterAssembly`.<br /><br /> Se questo parametro è specificato, i parametri `Assemblies` e `TypeLibFiles` verranno ignorati.|  
|`TypeLibFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Annulla la registrazione della libreria dei tipi indicata dall'assembly specificato. **Nota:** questo parametro è necessario solo se il nome dei file della libreria dei tipi non corrisponde a quello dell'assembly.|  
  
## <a name="remarks"></a>Note  
 Per la corretta esecuzione dell'attività non è necessario che l'assembly sia presente. Se si prova ad annullare la registrazione di un assembly inesistente, l'attività verrà comunque eseguita correttamente e verrà visualizzato un avviso. Questa situazione si verifica perché l'attività ha la funzione di rimuovere la registrazione dell'assembly dal Registro di sistema. Se l'assembly non esiste, non si trova nel Registro di sistema e l'attività viene pertanto eseguita correttamente.  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, che a sua volta eredita dalla classe <xref:System.MarshalByRefObject>. La classe `MarshalByRefObject` fornisce la stessa funzionalità della classe <xref:Microsoft.Build.Utilities.Task>, con la differenza che è possibile crearne un'istanza nel relativo dominio applicazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'attività `UnregisterAssembly` viene usata per annullare la registrazione dell'assembly eventualmente presente nel percorso specificato dalle proprietà `OutputPath` e `FileName`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <OutputPath>\Output\</OutputPath>  
        <FileName>MyFile.dll</FileName>  
    </PropertyGroup>  
    <Target Name="UnregisterAssemblies">  
        <UnregisterAssembly  
            Condition="Exists('$(OutputPath)$(FileName)')"  
            Assemblies="$(OutputPath)$(FileName)" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività RegisterAssembly](../msbuild/registerassembly-task.md)   
 [Tasks](../msbuild/msbuild-tasks.md)  (Attività)  
 [Task Reference](../msbuild/msbuild-task-reference.md) (Riferimento alle attività)
