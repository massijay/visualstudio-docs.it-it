---
title: "Task Writing | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, writing tasks"
  - "tasks, creating for MSBuild"
  - "MSBuild, creating tasks"
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Task Writing
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le attività forniscono il codice che viene eseguito durante il processo di compilazione.  Le attività sono contenute nelle destinazioni  Con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] viene fornita una libreria di attività più comuni, ma è possibile creare attività personalizzate.  Per ulteriori informazioni sulla libreria di attività fornita con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], vedere [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## Attività  
 Alcuni esempi di attività sono [Copy](../msbuild/copy-task.md), che consente di copiare uno o più file, [MakeDir](../msbuild/makedir-task.md), che consente di creare una directory e [Csc](../msbuild/csc-task.md), che consente di compilare il file con i codici sorgente in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  Ogni attività viene implementata come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>, definita nell'assembly Microsoft.Build.Framework.dll.  
  
 Per implementare un'attività, è possibile utilizzare due approcci diversi:  
  
-   Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ITask>.  
  
-   Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Task>, definita nell'assembly Microsoft.Build.Utilities.dll.  L'attività implementa ITask e fornisce le implementazioni predefinite di alcuni membri di ITask.  Inoltre, la registrazione è più semplice.  
  
 In entrambi i casi è necessario aggiungere alla propria classe un metodo denominato `Execute`, ossia il metodo che viene richiamato quando viene eseguita l'attività.  Questo metodo non assume alcun parametro e restituisce un valore `Boolean`: `true` se l'attività ha esito positivo oppure `false` se ha esito negativo.  Nell'esempio seguente è illustrata un'attività che non esegue alcuna azione e restituisce `true`.  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
        }  
    }  
}  
```  
  
 Il seguente file di progetto esegue questa attività:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyTarget">  
        <SimpleTask />  
    </Target>  
</Project>  
```  
  
 Quando le attività vengono eseguite, possono ricevere anche input dal file di progetto se si creano proprietà .NET nella classe dell'attività.  In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] queste proprietà vengono impostate immediatamente prima di chiamare il metodo `Execute` dell'attività.  Per creare una proprietà stringa utilizzare il codice attività, ad esempio:  
  
```  
using System;  
using Microsoft.Build.Framework;  
using Microsoft.Build.Utilities;  
  
namespace MyTasks  
{  
    public class SimpleTask : Task  
    {  
        public override bool Execute()  
        {  
            return true;  
         }  
  
        private string myProperty;  
        public string MyProperty  
        {  
            get { return myProperty; }  
            set { myProperty = value; }  
        }  
    }  
}  
```  
  
 Il seguente file di progetto esegue questa attività e imposta `MyProperty` con un determinato valore:  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MyProperty="Value for MyProperty" />  
   </Target>  
</Project>  
```  
  
## Registrazione delle attività  
 Se il progetto dovrà essere in grado di eseguire un'attività, è necessario specificare in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] come individuare l'assembly che contiene la classe dell'attività.  Le attività vengono registrate tramite [UsingTask Element \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
 Il file Microsoft.Common.Tasks di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è un file di progetto che contiene un elenco di elementi `UsingTask` che registrano tutte le attività fornite con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Questo file viene incluso automaticamente ogni volta che si compila un progetto.  Se l'attività registrata in Microsoft.Common.Tasks è anche registrata nel file di progetto corrente, il file di progetto corrente ha la precedenza, ossia è possibile sostituire un'attività predefinita con la propria attività avente lo stesso nome.  
  
> [!TIP]
>  Per visualizzare un elenco di attività fornite con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], visualizzare il contenuto di Microsoft.Common.Tasks.  
  
## Generazione di eventi da un'attività  
 Se l'attività deriva dalla classe di supporto <xref:Microsoft.Build.Utilities.Task>, è possibile utilizzare un metodo di supporto qualsiasi nella classe <xref:Microsoft.Build.Utilities.Task> per generare gli eventi che verranno intercettati e visualizzati da tutti i logger registrati:  
  
```  
public override bool Execute()  
{  
    Log.LogError("messageResource1", "1", "2", "3");  
    Log.LogWarning("messageResource2");  
    Log.LogMessage(MessageImportance.High, "messageResource3");  
    ...  
}  
```  
  
 Se l'attività implementa direttamente <xref:Microsoft.Build.Framework.ITask>, è comunque possibile generare tali eventi ma occorre utilizzare l'interfaccia IBuildEngine.  Nell'esempio riportato di seguito viene descritta un'attività che implementa ITask e genera un evento personalizzato:  
  
```  
public class SimpleTask : ITask  
{  
    private IBuildEngine buildEngine;  
    public IBuildEngine BuildEngine  
    {  
        get{ return buildEngine; }  
        set{ buildEngine = value; }  
    }  
  
    public override bool Execute()  
    {  
        TaskEventArgs taskEvent =  
            new TaskEventArgs(BuildEventCategory.Custom,  
            BuildEventImportance.High, "Important Message",  
           "SimpleTask");  
        BuildEngine.LogBuildEvent(taskEvent);  
        return true;  
    }  
}  
```  
  
## Impostazione di parametri di attività obbligatori  
 È possibile contrassegnare determinate proprietà dell'attività come "obbligatorie", in modo che tutti i file di progetto che eseguono l'attività debbano impostare i valori per tali proprietà, altrimenti la compilazione avrà esito negativo.  Applicare nel modo seguente l'attributo `[Required]` alla proprietà .NET nell'attività:  
  
```  
private string requiredProperty;  
  
[Required]  
public string RequiredProperty  
{  
    get { return requiredProperty; }  
    set { requiredProperty = value; }  
}  
```  
  
 L'attributo `[Required]` è definito da <xref:Microsoft.Build.Framework.RequiredAttribute> nello spazio dei nomi <xref:Microsoft.Build.Framework>.  
  
## Esempio  
  
### Descrizione  
 La seguente classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] illustra un'attività che deriva dalla classe di supporto <xref:Microsoft.Build.Utilities.Task>.  Questa attività restituisce `true`, ad indicare che ha avuto esito positivo.  
  
### Codice  
  
```  
using System;  
using Microsoft.Build.Utilities;  
  
namespace SimpleTask1  
{  
    public class SimpleTask1: Task  
    {  
        public override bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Esempio  
  
### Descrizione  
 La seguente classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] illustra un'attività che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>.  Questa attività restituisce `true`, ad indicare che ha avuto esito positivo.  
  
### Codice  
  
```  
using System;  
using Microsoft.Build.Framework;  
  
namespace SimpleTask2  
{  
    public class SimpleTask2: ITask  
    {  
        //When implementing the ITask interface, it is necessary to  
        //implement a BuildEngine property of type  
        //Microsoft.Build.Framework.IBuildEngine. This is done for  
        //you if you derive from the Task class.  
        private IBuildEngine buildEngine;  
        public IBuildEngine BuildEngine  
        {  
            get  
            {  
                return buildEngine;  
            }  
            set  
            {  
                buildEngine = value;  
            }  
         }  
  
        // When implementing the ITask interface, it is necessary to  
        // implement a HostObject property of type Object.  
        // This is done for you if you derive from the Task class.  
        private Object hostObject;  
        public Object HostObject  
        {  
            get  
            {  
                return hostObject;  
            }  
  
            set  
            {  
                hostObject = value;  
            }  
        }  
  
        public bool Execute()  
        {  
            // This is where the task would presumably do its work.  
            return true;  
        }  
    }  
}  
```  
  
## Esempio  
  
### Descrizione  
 La seguente classe di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] illustra un'attività che deriva dalla classe di supporto <xref:Microsoft.Build.Utilities.Task>.  Ha una proprietà stringa obbligatoria e genera un evento che viene visualizzato da tutti i logger registrati.  
  
### Codice  
 [!code-cs[msbuild_SimpleTask3#1](../msbuild/codesnippet/CSharp/task-writing_1.cs)]  
  
## Esempio  
  
### Descrizione  
 Nell'esempio riportato di seguito viene illustrato un file di progetto che richiama l'attività dell'esempio precedente, SimpleTask3.  
  
### Codice  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <UsingTask TaskName="SimpleTask3.SimpleTask3"   
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>  
  
    <Target Name="MyTarget">  
        <SimpleTask3 MyProperty="Hello!"/>  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)