---
title: "How to: Clean a Build | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, cleaning a build"
  - "directories [.NET Framework], for output items"
  - "output, removing items"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# How to: Clean a Build
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si pulisce una compilazione, tutti i file intermedi e di output vengono eliminati e rimangono solo i file di progetto e di componente.  Da tali file è quindi possibile compilare nuove istanze di file intermedi e di output.  La libreria di attività comuni fornita con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include un'attività [Exec](../msbuild/exec-task.md) che può essere utilizzata per eseguire i comandi di sistema.  Per ulteriori informazioni sulla libreria di attività, vedere [Task Reference](../msbuild/msbuild-task-reference.md).  
  
## Creazione di una directory per gli elementi di output  
 Per impostazione predefinita, il file con estensione exe creato al momento della compilazione di un progetto viene memorizzato nella stessa directory dei file di progetto e di origine.  In genere, tuttavia, gli elementi di output vengono creati in una directory separata.  
  
#### Per creare una directory per gli elementi di output  
  
1.  Utilizzare l'elemento `Property` per definire il percorso e il nome della directory.  Creare ad esempio una directory con nome `BuiltApp` nella directory che contiene i file di progetto e di origine:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Se la directory non esiste, utilizzare l'attività [MakeDir](../msbuild/makedir-task.md) per crearla.  Di seguito è riportato un esempio:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## Rimozione degli elementi di output  
 Prima di creare nuove istanze dei file intermedi e di output, è possibile eliminare tutte le precedenti istanze di tali file.  Per eliminare da un disco una directory e tutti i file e le directory in essa contenuti, utilizzare l'attività [RemoveDir](../msbuild/removedir-task.md).  
  
#### Per eliminare una directory e tutti i file in essa contenuti  
  
-   Per eliminare la directory, utilizzare l'attività `RemoveDir`.  Di seguito è riportato un esempio:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## Esempio  
 Nell'esempio di codice riportato di seguito è presente una nuova destinazione, `Clean`, che utilizza l'attività `RemoveDir` per eliminare una directory e tutti i file e le directory in essa contenuti.  In questo esempio, inoltre, la destinazione `Compile` crea una directory separata per gli elementi di output che vengono eliminati quando la compilazione viene pulita.  
  
 `Compile` viene definita come destinazione predefinita e viene, quindi, utilizzata automaticamente, a meno che si specifichino una o più destinazioni diverse.  Per specificare una destinazione diversa, utilizzare l'opzione della riga di comando **\/target**.  Di seguito è riportato un esempio:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 L'opzione **\/target** può essere abbreviata in **\/t** e applicata per specificare più di una destinazione.  Per utilizzare ad esempio la destinazione `Clean` e quindi la destinazione `Compile`, digitare:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Exec Task](../msbuild/exec-task.md)   
 [MakeDir Task](../msbuild/makedir-task.md)   
 [RemoveDir Task](../msbuild/removedir-task.md)   
 [Csc Task](../msbuild/csc-task.md)   
 [Targets](../msbuild/msbuild-targets.md)