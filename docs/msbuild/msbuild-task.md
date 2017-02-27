---
title: "Attivit&#224; MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#MSBuild"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild (attività) [MSBuild]"
  - "MSBuild, MSBuild (attività)"
ms.assetid: 76577f6c-7669-44ad-a840-363e37a04d34
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Attivit&#224; MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Compila progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] da un altro progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `MSBuild`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`BuildInParallel`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i progetti specificati nel parametro `Projects` vengono compilati in parallelo, se consentito.  Il valore predefinito è `false`.|  
|`Projects`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file di progetto da compilare.|  
|`Properties`|Parametro `String` facoltativo.<br /><br /> Elenco delimitato da punti e virgola di coppie di nomi e valori di proprietà da applicare come proprietà globali al progetto figlio.  Dal punto di vista funzionale, la specifica di questo parametro equivale a impostare le proprietà mediante l'opzione **\/property** durante la compilazione con [MSBuild.exe](../msbuild/msbuild-command-line-reference.md).  Ad esempio:<br /><br /> `Properties="Configuration=Debug;Optimize=$(Optimize)"`<br /><br /> Quando si passano proprietà al progetto tramite il parametro `Properties`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crea un'istanza nuova del progetto anche se il file di progetto è già stato caricato.  Quando una nuova istanza del progetto è stata creata, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] la tratta come un progetto diverso che ha proprietà globali diverse e che può essere compilato in parallelo con le altre istanze del progetto.  Ad esempio, una configurazione di rilascio compilata contemporaneamente a una configurazione di debug.|  
|`RebaseOutputs`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, i percorsi relativi degli elementi di output di destinazione dei progetti compilati vengono modificati in base alla posizione del progetto chiamante.  Il valore predefinito è `false`.|  
|`RemoveProperties`|Parametro `String` facoltativo.<br /><br /> Specifica il set di proprietà globali da rimuovere.|  
|`RunEachTargetSeparately`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] richiama ogni destinazione nell'elenco passato a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] una alla volta, anziché contemporaneamente.  Impostando questo parametro su `true`, le destinazioni successive vengono richiamate anche se le precedenti chiamate alle destinazioni non sono riuscite.  In caso contrario, un errore di compilazione arresterebbe la chiamata di tutte le destinazioni successive.  Il valore predefinito è `false`.|  
|`SkipNonexistentProjects`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, che non sono presenti sul disco verranno ignorati.  In caso contrario, tali progetti causeranno un errore.|  
|`StopOnFirstFailure`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, quando uno dei progetti non viene compilato, non verrà compilato nessun altro progetto.  Attualmente questa opzione non è supportata quando si esegue la compilazione in parallelo \(con più processori\).|  
|`TargetAndPropertyListSeparators`|Parametro `String[]` facoltativo.<br /><br /> Specifica un elenco di destinazioni e proprietà come metadati dell'elemento `Project`\).  I caratteri dei separatori verranno modificati in caratteri non di escape prima dell'elaborazione.  ad.. esempio %3B \(utilizzato caratteri di escape "; "\) verrà considerato come se fosse non utilizzare caratteri di escape "; ".|  
|`TargetOutputs`|Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Restituisce gli output delle destinazioni compilate di tutti i file di progetto.  Vengono restituiti solo gli output delle destinazioni specificate, non quelli che possono essere presenti nelle destinazioni da cui dipendono quelle specificate.<br /><br /> Il parametro `TargetOutputs` contiene anche i seguenti metadati:<br /><br /> -   `MSBuildSourceProjectFile`: file di progetto di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] contenente la destinazione che ha impostato gli output.<br />-   `MSBuildSourceTargetName`: destinazione che ha impostato gli output. **Note:**  Per identificare individualmente gli output di ciascun file di progetto o destinazione, è necessario eseguire l'attività `MSBuild` separatamente per ogni file di progetto o destinazione.  Se si esegue l'attività `MSBuild` una sola volta per compilare tutti i file di progetto, gli output di tutte le destinazioni vengono raccolti in un'unica matrice.|  
|`Targets`|Parametro `String` facoltativo.<br /><br /> Specifica le destinazioni da compilare nei file di progetto.  Utilizzare un punto e virgola per separare un elenco di nomi di destinazioni.  Se nell'attività `MSBuild` non viene specificata alcuna destinazione, vengono compilate le destinazioni predefinite specificate nei file di progetto. **Note:**  È necessario che le destinazioni siano incluse in tutti i file di progetto.  In caso contrario, si verifica un errore di compilazione.|  
|`ToolsVersion`|Parametro `String` facoltativo.<br /><br /> Specifica l'attributo `ToolsVersion` da utilizzare quando si compilano progetti passati a questa attività.<br /><br /> Consente a un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di compilare un progetto che utilizza come destinazione una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] diversa da quella specificata nel progetto.  I valori validi sono `2.0`, `3.0` e `3.5`.  Il valore predefinito è `3.5`.|  
|`UnloadProjectsOnCompletion`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il progetto verrà scaricato una volta completata l'operazione.|  
|`UseResultsCache`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene restituito il risultato memorizzato nella cache, se presente.  Se viene eseguita l'attività theMSBuild, il risultato sarà memorizzato nella cache in un ambito \(ProjectFileName, GlobalProperties\) \[TargetNames\]<br /><br /> come elenco elementi di compilazione|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Anziché utilizzare [Exec Task](../msbuild/exec-task.md) per avviare MSBuild.exe, questa attività utilizza lo stesso processo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per la compilazione di progetti figlio.  L'elenco di destinazioni già compilate che è possibile ignorare viene condiviso dalle compilazioni padre e figlio.  Questa attività risulta inoltre più rapida perché non vengono creati nuovi processi [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Mediante questa attività è possibile elaborare non solo file di progetto, ma anche file di soluzione.  
  
 Qualsiasi configurazione richiesta da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] per consentire la compilazione simultanea dei progetti, anche se la configurazione utilizza un'infrastruttura remota \(ad esempio, porte, protocolli, timeout, tentativi e così via\), deve essere resa configurabile utilizzando un file di configurazione.  Se possibile, gli elementi di configurazione devono poter essere specificati come parametri sull'attività `MSBuild`.  
  
 A partire da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, i progetti di soluzione evidenziano i TargetOutputs da tutti i sottoprogetti compilati.  
  
## Passaggio delle proprietà ai progetti  
 Nelle versioni di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] precedenti a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, il passaggio di set di proprietà diversi ai vari progetti elencati nell'elemento [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] era un'operazione complicata.  Se è stato utilizzato l'attributo Properties dell'[MSBuild Task](../msbuild/msbuild-task.md), l'impostazione è stata applicata a tutti i progetti compilati a meno che l'[MSBuild Task](../msbuild/msbuild-task.md) non sia stata eseguita in batch e non siano state fornite su condizione proprietà diverse per ogni progetto nell'elenco degli elementi.  
  
 Tuttavia, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5 fornisce due nuovi elementi riservati dei metadati, Properties e AdditionalProperties che forniscono una modalità flessibile per passare proprietà diverse per progetti diversi compilati mediante l'[MSBuild Task](../msbuild/msbuild-task.md).  
  
> [!NOTE]
>  Questi nuovi elementi dei metadati sono applicabili solo agli elementi passati nell'attributo Projects dell'[MSBuild Task](../msbuild/msbuild-task.md).  
  
## Vantaggi della compilazione multiprocessore  
 Uno dei principali vantaggi derivanti dall'utilizzo di questi nuovi metadati si può constatare quando si compilano i progetti in parallelo su un sistema multiprocessore.  I metadati consentono di consolidare tutti i progetti in una sola chiamata dell'[MSBuild Task](../msbuild/msbuild-task.md) senza dover eseguire alcuna attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] batch o condizionale.  Quando si chiama una sola [MSBuild Task](../msbuild/msbuild-task.md), tutti i progetti elencati nell'attributo Projects saranno compilati in parallelo.  Tuttavia, solo se l'attributo `BuildInParallel=true` è presente in [MSBuild Task](../msbuild/msbuild-task.md). Per ulteriori informazioni, vedere [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## Metadati delle proprietà  
 In uno scenario comune, più file della soluzione vengono compilati utilizzando l'[MSBuild Task](../msbuild/msbuild-task.md) esclusivamente tramite configurazioni della build differenti.  È possibile che si debba compilare la soluzione a1 utilizzando la configurazione di debug e la soluzione a2 utilizzando la configurazione di rilascio.  In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, il file di progetto sarebbe come segue:  
  
> [!NOTE]
>  Nell'esempio seguente, "…" rappresenta i file della soluzione aggiuntivi.  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln..." Properties="Configuration=Debug"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
 Utilizzando i metadati Properties, tuttavia, è possibile semplificare l'operazione al fine di utilizzare una sola [MSBuild Task](../msbuild/msbuild-task.md), come mostrato di seguito:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <Properties>Configuration=Debug</Properties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"/>  
    </Target>  
</Project>  
```  
  
 \- oppure \-  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…"/>  
        <ProjectToBuild Include="a2.sln">  
            <Properties>Configuration=Release</Properties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Debug"/>  
    </Target>  
</Project>  
```  
  
## Metadati AdditionalProperties  
 Si consideri lo scenario seguente in cui si stanno compilando due file di soluzione utilizzando l'[MSBuild Task](../msbuild/msbuild-task.md); entrambi utilizzano la configurazione di rilascio, ma uno impiega l'architettura x86 e l'altro l'architettura ia64.  In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0, sarebbe necessario creare più istanze dell'[MSBuild Task](../msbuild/msbuild-task.md): una per compilare il progetto utilizzando la configurazione di rilascio con l'architettura x86, l'altro utilizzando la configurazione di rilascio con l'architettura ia64.  Il file di progetto sarebbe come segue:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Build">  
        <MSBuild Projects="a1.sln…" Properties="Configuration=Release;   
          Architecture=x86"/>  
        <MSBuild Projects="a2.sln" Properties="Configuration=Release;   
          Architecture=ia64"/>  
    </Target>  
</Project>  
```  
  
 Utilizzando i metadati AdditionalProperties, è possibile semplificare l'operazione al fine di usare una sola [MSBuild Task](../msbuild/msbuild-task.md) come indicato di seguito:  
  
### a.proj  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ProjectToBuild Include="a1.sln…">  
            <AdditionalProperties>Architecture=x86  
              </AdditionalProperties>  
        </ProjectToBuild>  
        <ProjectToBuild Include="a2.sln">  
            <AdditionalProperties>Architecture=ia64  
              </AdditionalProperties>  
        </ProjectToBuild>  
    </ItemGroup>  
    <Target Name="Build">  
        <MSBuild Projects="@(ProjectToBuild)"   
          Properties="Configuration=Release"/>  
    </Target>  
</Project>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `MSBuild` viene utilizzata per compilare i progetti specificati dalla raccolta di elementi `ProjectReferences`.  Gli output di destinazione ottenuti vengono archiviati nella raccolta di elementi `AssembliesBuiltByChildProjects`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ProjectReferences Include="*.*proj" />  
    </ItemGroup>  
  
    <Target Name="BuildOtherProjects">  
        <MSBuild  
            Projects="@(ProjectReferences)"  
            Targets="Build">  
            <Output  
                TaskParameter="TargetOutputs"  
                ItemName="AssembliesBuiltByChildProjects" />  
        </MSBuild>  
    </Target>  
  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)