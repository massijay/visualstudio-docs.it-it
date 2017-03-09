---
title: "RegisterAssembly Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, RegisterAssembly task"
  - "RegisterAssembly task [MSBuild]"
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RegisterAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legge i metadati all'interno dell'assembly specificato e aggiunge le voci necessarie al Registro di sistema, consentendo ai client COM di creare classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] in modo trasparente.  Il comportamento di questa attività è simile, ma non identico, a quello dello [Regasm.exe \(Assembly Registration Tool\)](../Topic/Regasm.exe%20\(Assembly%20Registration%20Tool\).md).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `RegisterAssembly`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Assemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli assembly da registrare con COM.|  
|`AssemblyListFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Contiene informazioni sullo stato tra l'attività `RegisterAssembly` e l'attività [UnregisterAssembly](../msbuild/unregisterassembly-task.md).  Queste informazioni possono essere utilizzate per evitare che l'attività `UnregisterAssembly` tenti di annullare la registrazione di un assembly che non è riuscito a eseguire la registrazione nell'attività `RegisterAssembly`.|  
|`CreateCodeBase`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, viene creata una voce della base di codici nel Registro di sistema, che specifica il percorso di un assembly non installato nella Global Assembly Cache.  È consigliabile non specificare questa opzione se successivamente si intende installare nella Global Assembly Cache l'assembly che si sta registrando.|  
|`TypeLibFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica la libreria dei tipi da generare dall'assembly specificato.  La libreria dei tipi generata contiene le definizioni dei tipi accessibili definiti all'interno dell'assembly.  La libreria dei tipi viene generata solo se viene soddisfatta una delle seguenti condizioni:<br /><br /> -   Nel percorso specificato non è presente una libreria dei tipi con lo stesso nome.<br />-   La libreria dei tipi esistente è precedente all'assembly passato.<br /><br /> Se la libreria dei tipi è successiva all'assembly passato, non ne verrà creata una nuova ma l'assembly verrà comunque registrato.<br /><br /> Se questo parametro è specificato, è necessario che presenti lo stesso numero di elementi del parametro `Assemblies` affinché l'attività abbia esito positivo.  Se non è specificato alcun valore, il nome dell'assembly verrà utilizzato per impostazione predefinita e l'estensione dell'elemento verrà modificata in tlb.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `RegisterAssembly` viene utilizzata per registrare l'assembly specificato dalla raccolta di elementi `MyAssemblies`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="MyAssembly.dll" />  
    <ItemGroup>  
  
    <Target Name="RegisterAssemblies">  
        <RegisterAssembly  
            Assemblies="@(MyAssemblies)" >  
    </Target>  
  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)