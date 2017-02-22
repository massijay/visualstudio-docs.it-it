---
title: "Error Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error task [MSBuild]"
  - "MSBuild, Error task"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Error Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Interrompe una compilazione e registra un errore in base a un'istruzione condizionale valutata.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `Error`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Code`|Parametro `String` facoltativo.<br /><br /> Codice da associare all'errore.|  
|`File`|Parametro `String` facoltativo.<br /><br /> Nome del file in cui è contenuto l'errore.  Se non viene fornito alcun nome file, viene utilizzato il file in cui è contenuta l'attività Error.|  
|`HelpKeyword`|Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'errore.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Testo dell'errore registrato in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se il parametro `Condition` restituisce `true`.|  
  
## Note  
 L'attività `Error` consente al progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di inviare il testo dell'errore ai logger e di interrompere l'esecuzione della compilazione.  
  
 Se il parametro `Condition` restituisce `true`, la compilazione viene interrotta e viene registrato un errore.  Se non esiste un parametro `Condition`, viene registrato l'errore e l'esecuzione della compilazione viene interrotta.  Per ulteriori informazioni sulla registrazione, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene verificato che siano impostate tutte le proprietà necessarie.  In caso contrario, il progetto genera un evento di errore e registra il valore del parametro `Text` dell'attività `Error`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)