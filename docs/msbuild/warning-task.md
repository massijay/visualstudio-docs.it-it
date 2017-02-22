---
title: "Warning Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Warning task [MSBuild]"
  - "MSBuild, Warning task"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Warning Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Registra un avviso durante una compilazione in base a un'istruzione condizionale valutata.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `Warning`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Code`|Parametro `String` facoltativo.<br /><br /> Codice da associare all'avviso.|  
|`File`|Parametro `String` facoltativo.<br /><br /> Specifica il file rilevante, se presente.  Se non viene fornito alcun file, viene utilizzato il file in cui è contenuta l'attività Warning.|  
|`HelpKeyword`|Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'avviso.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Testo dell'avviso registrato in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se il parametro `Condition` restituisce `true`.|  
  
## Note  
 L'attività `Warning` consente ai progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di verificare la presenza di una configurazione o di una proprietà richiesta prima di passare all'istruzione di compilazione successiva.  
  
 Se il parametro `Condition` dell'attività `Warning` restituisce `true`, viene registrato il valore del parametro `Text` e la compilazione continua a essere eseguita.  Se il parametro `Condition` non esiste, viene registrato il testo dell'avviso.  Per ulteriori informazioni sulla registrazione, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio di codice riportato di seguito vengono verificate le proprietà impostate sulla riga di comando.  Se non è stata impostata alcuna proprietà, il progetto genera un evento di avviso e registra il valore del parametro `Text` dell'attività `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Vedere anche  
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)