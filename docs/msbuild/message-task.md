---
title: "Attività Message | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 23
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
ms.openlocfilehash: e2c4a65b44ea3cdc9ed54911e8037467e5ce5554
ms.lasthandoff: 02/22/2017

---
# <a name="message-task"></a>Attività Message
Registra un messaggio durante una compilazione.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Message`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Importance`|Parametro `String` facoltativo.<br /><br /> Specifica l'importanza del messaggio. Il valore di questo parametro può essere `high`, `normal` o `low`. Il valore predefinito è `normal`.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Testo dell'errore da registrare.|  
  
## <a name="remarks"></a>Note  
 L'attività `Message` consente ai progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di inviare messaggi ai logger in fasi diverse del processo di compilazione.  
  
 Se il parametro `Condition` restituisce `true`, verrà registrato il valore del parametro `Text` e la compilazione continuerà a essere eseguita. Se il parametro `Condition` non esiste, verrà registrato il testo del messaggio. Per altre informazioni sulla registrazione, vedere [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione).  
  
 Per impostazione predefinita, il messaggio viene inviato al logger di console di MSBuild. Tale comportamento può essere modificato impostando il parametro <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. Il parametro `Importance` viene interpretato dal logger.  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di tali parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md) (Classe di base TaskExtension).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice riportato di seguito i messaggi vengono registrati in tutti i logger registrati.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione)
