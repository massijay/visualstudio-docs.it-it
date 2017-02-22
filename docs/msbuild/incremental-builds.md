---
title: "Incremental Builds | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, incremental builds"
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Incremental Builds
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le compilazioni incrementali sono compilazioni ottimizzate affinché le destinazioni aventi file di output aggiornati rispetto ai relativi file di input corrispondenti non vengano eseguite.  Un elemento di destinazione può presentare sia un attributo `Inputs`, che indica gli elementi che la destinazione accetta come input, sia un attributo `Outputs`, che indica gli elementi che produce come output.  MSBuild tenta di trovare un mapping 1 a 1 tra i valori di questi attributi.  Se tale mapping esiste, MSBuild confronta il timestamp di ogni elemento di input con il timestamp dell'elemento di output corrispondente.  I file di output che non presentano alcun mapping 1 a 1 vengono confrontati con tutti i file di input.  Un elemento viene considerato aggiornato se il relativo file di output presenta un timestamp identico o più nuovo di quello dei relativi file di input.  
  
 Se tutti gli elementi di output sono aggiornati, MSBuild ignora la destinazione.  Questa *compilazione incrementale* della destinazione può migliorare significativamente la velocità di compilazione.  Se solo alcuni dei file sono aggiornati, MSBuild esegue la destinazione ma ignora gli elementi aggiornati e, in questo modo, aggiorna tutti gli elementi.  Questo processo è noto come *compilazione incrementale parziale*.  
  
 I mapping 1 a 1 in genere vengono prodotti dalle trasformazioni degli elementi.  Per ulteriori informazioni, vedere [Transforms](../msbuild/msbuild-transforms.md).  
  
 Si consideri la destinazione seguente.  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Il set dei file rappresentati dal tipo di elemento `Compile` viene copiato in una directory di backup.  I file di backup presentano l'estensione BAK.  Se i file rappresentati dal tipo di elemento `Compile` o i file di backup corrispondenti non vengono eliminati o modificati dopo l'esecuzione della destinazione Backup, quest'ultima viene ignorata nelle compilazioni successive.  
  
## Inferenza di output  
 MSBuild confronta gli attributi `Inputs` e `Outputs` di una destinazione per determinare se quest'ultima deve essere eseguita.  Idealmente, il set di file esistente dopo il completamento di una compilazione incrementale deve rimanere lo stesso sia le destinazioni associate vengono eseguite sia se vengono ignorate.  Poiché le proprietà e gli elementi creati o modificati dalle attività possono influire sulla compilazione, MSBuild deve inferirne i valori anche se la destinazione che influisce su essi viene ignorata.  Questo processo è noto come *inferenza di output*.  
  
 Vi sono tre casi:  
  
-   La destinazione presenta un attributo `Condition` che risulta essere `false`.  In questo caso, la destinazione non viene eseguita e non influisce sulla compilazione.  
  
-   La destinazione presenta output non aggiornati e viene eseguita affinché vengano aggiornati.  
  
-   Tutti gli output della destinazione sono aggiornati e pertanto la destinazione viene ignorata.  MSBuild valuta la destinazione e apporta modifiche a elementi e proprietà come se la destinazione fosse stata eseguita.  
  
 Per supportare la compilazione incrementale, le attività devono garantire che il valore dell'attributo `TaskParameter` di qualsiasi elemento `Output` sia uguale a un parametro di input delle attività.  Di seguito sono riportati alcuni esempi:  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Ciò comporta la creazione della proprietà Easy, che presenta il valore "123" sia se la destinazione viene eseguita sia se viene ignorata.  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Ciò comporta la creazione del tipo di elemento Simple, che presenta i due elementi "a.cs" e "b.cs" sia se la destinazione viene eseguita sia se viene ignorata.  
  
 In MSBuild 3.5, l'inferenza di output viene eseguita automaticamente sui gruppi di proprietà ed elementi in un target.  Le attività `CreateItem` non sono necessarie in una destinazione ed è opportuno evitarne l'esecuzione.  Inoltre, le attività `CreateProperty` devono essere utilizzate in una destinazione solo per determinare se quest'ultima è stata eseguita.  
  
## Come determinare se una destinazione è stata eseguita  
 A causa dell'inferenza di output, è necessario aggiungere un'attività `CreateProperty` a una destinazione per esaminare proprietà ed elementi allo scopo di poter determinare se la destinazione è stata eseguita.  Aggiungere l'attività `CreateProperty` alla destinazione e aggiungervi un elemento `Output` il cui `TaskParameter` è "ValueSetByTask".  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Ciò consente di creare la proprietà CompileRan e di assegnare a quest'ultima il valore `true`, ma solo se la destinazione viene eseguita.  Se la destinazione viene ignorata, la proprietà CompileRan non viene creata.  
  
## Vedere anche  
 [Targets](../msbuild/msbuild-targets.md)