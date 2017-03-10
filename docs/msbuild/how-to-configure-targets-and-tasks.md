---
title: "Procedura: Configurare destinazioni e attività | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
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
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>Procedura: Configurare destinazioni e attività
Alcune attività MSBuild possono essere impostate in modo da essere eseguite nell'ambiente a cui sono destinate, indipendentemente dall'ambiente del computer di sviluppo. Se ad esempio si usa un computer a 64 bit per creare un'applicazione destinata a un'architettura a 32 bit, le attività selezionate vengono eseguite in un processo a 32 bit.  
  
> [!NOTE]
>  Se un'attività di compilazione è scritta in un linguaggio .NET, ad esempio in Visual C# o Visual Basic, e non usa strumenti o risorse native, potrà essere eseguita in qualsiasi contesto di destinazione senza adattamento.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>Attributi UsingTask e parametri dell'attività  
 Gli attributi `UsingTask` seguenti interessano tutte le operazioni di un'attività in un determinato processo di compilazione:  
  
-   L'attributo `Runtime`, se presente, imposta la versione CLR (Common Language Runtime) e può assumere uno dei valori seguenti: `CLR2`, `CLR4`, `CurrentRuntime` o `*` (qualsiasi runtime).  
  
-   L'attributo `Architecture`, se presente, imposta la piattaforma e il numero di bit e può assumere uno dei valori seguenti: `x86`, `x64`, `CurrentArchitecture` o `*` (qualsiasi architettura).  
  
-   L'attributo `TaskFactory`, se presente, imposta la factory delle attività che crea ed esegue l'istanza dell'attività e può assumere solo il valore `TaskHostFactory`. Per altre informazioni, vedere la sezione Factory delle attività più avanti in questo documento.  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Per impostare il contesto di destinazione di una singola attività è possibile usare anche i parametri `MSBuildRuntime` e `MSBuildArchitecture`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Prima di eseguire un'attività, MSBuild cerca un attributo `UsingTask` corrispondente con lo stesso contesto di destinazione.  Deve essere trovata una corrispondenza anche per i parametri specificati in `UsingTask` ma non nell'attività corrispondente,  così come per i parametri specificati nell'attività ma non nell'attributo `UsingTask` corrispondente. Se non sono stati specificati valori di parametro né per `UsingTask` né per l'attività, l'impostazione predefinita dei valori è `*` (qualsiasi parametro).  
  
> [!WARNING]
>  Se sono presenti più elementi `UsingTask` e hanno tutti attributi `TaskName`, `Runtime` e `Architecture` corrispondenti, l'ultimo da valutare sostituisce gli altri.  
  
 Se sono stati impostati parametri nell'attività, MSBuild tenta di trovare un elemento `UsingTask` che corrisponda, o almeno non sia in conflitto, con i parametri impostati.  È possibile che più elementi `UsingTask` specifichino il contesto di destinazione per la stessa attività.  Un'attività con vari file eseguibili per diversi ambienti di destinazione, ad esempio, avrebbe un aspetto simile al seguente:  
  
```xml  
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
  
## <a name="task-factories"></a>Factory delle attività  
 Prima di eseguire un'attività, MSBuild verifica di essere stato designato per l'esecuzione nel contesto software corrente.  In questo caso, MSBuild passa l'attività a AssemblyTaskFactory, che la esegue nel processo corrente; in caso contrario, MSBuild passa l'attività a TaskHostFactory, che la esegue in un processo corrispondente al contesto di destinazione. Anche se il contesto corrente e il contesto di destinazione corrispondono, è possibile imporre l'esecuzione out-of-process di un'attività (per motivi di isolamento, sicurezza o di altri tipo) impostando `TaskFactory` su `TaskHostFactory`.  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Parametri fantasma dell'attività  
 Come qualsiasi altro parametro dell'attività, `MSBuildRuntime` e `MSBuildArchitecture` possono essere impostati dalle proprietà di compilazione.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
