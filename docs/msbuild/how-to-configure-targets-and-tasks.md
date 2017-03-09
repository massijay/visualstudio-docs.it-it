---
title: "How to: Configure Targets and Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Configure Targets and Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le attività MSBuild selezionati possono essere impostati l ' ambiente che riguardano, indipendentemente dall' ambiente del computer di sviluppo.  Ad esempio, quando si utilizza un computer a 64 bit per compilare un'applicazione destinata all'architettura a 32 bit, le attività selezionate vengono eseguite in un processo a 32 bit.  
  
> [!NOTE]
>  Se un'attività di compilazione viene scritta in un linguaggio.NET, ad esempio Visual c\# o Visual Basic e non utilizzano risorse native o strumenti, quindi verrà eseguita nel contesto di destinazione senza adattamento.  
  
## Attributi e parametri di attività UsingTask  
 I seguenti attributi di `UsingTask` influiscono su tutte le operazioni di un'attività in un processo di compilazione specifico:  
  
-   L'attributo di `Runtime` , se presente, impostare la versione \(CLR\) di Common Language Runtime e può eseguire uno di questi valori: `CLR2`, `CLR4`, `CurrentRuntime`, o `*` \(qualsiasi runtime\).  
  
-   L'attributo di `Architecture` , se presente, impostare la piattaforma e il numero di bit e può eseguire uno di questi valori: `x86`, `x64`, `CurrentArchitecture`, o `*` \(qualsiasi architettura\).  
  
-   L'attributo di `TaskFactory` , se presente, impostare la factory delle attività che crea ed esegue l'istanza dell' attività e accetta solo il valore `TaskHostFactory`.  Per ulteriori informazioni, vedere le factory delle attività più avanti in questo documento.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 È inoltre possibile utilizzare i parametri di `MSBuildArchitecture` e di `MSBuildRuntime` per impostare il contesto di destinazione di una singola attività.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Prima di MSBuild esegue un'attività, cerca una corrispondenza `UsingTask` con lo stesso contesto di destinazione.  I parametri specificati in `UsingTask` ma non nell' attività corrispondente vengono considerati essere individuati.  I parametri specificati nell' attività ma non in `UsingTask` corrispondente vengono considerati essere individuati.  Se i valori dei parametri non sono specificati in `UsingTask` o nell' attività, l'impostazione predefinita di valori a `*` \(qualsiasi parametro\).  
  
> [!WARNING]
>  Se più di un `UsingTask` esiste e includono tutti `TaskName`corrispondente, `Runtime`e attributi di `Architecture` , l'ultimo da valutare sostituire gli altri.  
  
 Se i parametri vengono impostati sull' attività, MSBuild tenta di trovare almeno `UsingTask` corrispondente ai parametri o, non in conflitto tra loro.  Più di un `UsingTask` possibile specificare il contesto della stessa attività.  Ad esempio, un'attività che presenta eseguibili differenti per gli ambienti di destinazione diversi potrebbe essere simile al seguente:  
  
```  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## Factory delle attività  
 Prima di eseguire un'attività, controlli MSBuild da verificare se è definita da eseguire nel contesto corrente del software.  Se l'attività viene così definita, MSBuild la passa al AssemblyTaskFactory, che viene quindi eseguito nel processo corrente; in caso contrario, MSBuild passa l'attività a TaskHostFactory, che esegue l'attività in un processo corrispondente al contesto di destinazione.  Anche se il contesto corrente e la corrispondenza di destinazione di contesto, è possibile forzare un'attività eseguire out\-of\-process \(per l'isolamento, sicurezza, o altri motivi\) impostando `TaskFactory` a `TaskHostFactory`.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## Parametri dell' attività fittizi  
 Come tutti gli altri parametri dell' attività, `MSBuildRuntime` e `MSBuildArchitecture` è possibile impostare le proprietà di compilazione.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 A differenza di altri parametri delle attività, `MSBuildRuntime` e `MSBuildArchitecture` non sono evidenti all' attività stessa.  Per scrivere un'attività che è consapevole del contesto in cui è in esecuzione, è necessario verificare il contesto chiamando .NET Framework, o utilizzare le proprietà di compilazione per comunicare le informazioni sul contesto con altri parametri delle attività.  
  
> [!NOTE]
>  gli attributi di`UsingTask` possono essere impostate le proprietà dell' ambiente e set di strumenti.  
  
 I parametri di `MSBuildArchitecture` e di `MSBuildRuntime` forniscono una modalità più flessibile impostare il contesto di destinazione, ma anche il più ristretto in.  Da un lato, perché sono impostati sull' istanza stessa di attività e non vengono valutati finché l'attività non è accinga per ' esecuzione, possono derivare il relativo valore dall' ambito completo delle proprietà disponibili sia in valutazione\-ora che in fase di compilazione.  Di altra parte, questi parametri vengono applicate solo a una determinata istanza di un'attività in una particolare destinazione.  
  
> [!NOTE]
>  I parametri delle attività vengono valutati nel contesto del nodo padre, non nel contesto dell' host delle attività. Le variabili di ambiente che sono tempo di esecuzione o dipendente di architettura \(come il percorso dei file di programma\) valuteranno al valore corrispondente al nodo padre.  Tuttavia, se la stessa variabile di ambiente viene eseguita direttamente dall' attività, correttamente verranno valutati nel contesto dell' host delle attività.  
  
## Vedere anche  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)