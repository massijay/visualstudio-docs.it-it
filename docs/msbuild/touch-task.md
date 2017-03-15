---
title: "Attività Touch | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
caps.latest.revision: 17
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
ms.openlocfilehash: 940303589c14ed2f8aed0477e09d8a51b7a97d8f
ms.lasthandoff: 02/22/2017

---
# <a name="touch-task"></a>Attività Touch
Imposta l'ora di accesso e di modifica dei file.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Touch`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AlwaysCreate`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, crea file non ancora esistenti.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica la raccolta di file di cui aggiornare il timestamp.|  
|`ForceTouch`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, forza l'aggiornamento del timestamp anche se i file sono di sola lettura.|  
|`Time`|Parametro `String` facoltativo.<br /><br /> Specifica un'ora diversa da quella corrente. È necessario che il formato possa essere accettato dal metodo <xref:System.DateTime.Parse%2A>.|  
|`TouchedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene la raccolta di elementi di cui è stato eseguito l'aggiornamento del timestamp.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di tali parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'attività `Touch` viene usata per modificare l'ora di accesso e di modifica dei file specificati nella raccolta di elementi `Files` e per inserire l'elenco dei file di cui è stato eseguito l'aggiornamento del timestamp nella raccolta di elementi `FilesTouched`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
<ItemGroup>  
    <Files Include="File1.cs;File2.cs;File3.cs" />  
</ItemGroup>  
  
    <Target Name="TouchFiles">  
        <Touch  
            Files="@(Files)">  
            <Output  
                TaskParameter="TouchedFiles"  
                ItemName="FilesTouched"/>  
    </Touch>  
</Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)  (Attività)  
 [Task Reference](../msbuild/msbuild-task-reference.md) (Riferimento alle attività)
