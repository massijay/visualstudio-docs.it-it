---
title: "Task Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Task element [MSBuild]"
  - "<Task> element [MSBuild]"
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Task Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea ed esegue un'istanza di un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Il nome dell'elemento è determinato dal nome dell'attività che viene creata.  
  
## Sintassi  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo.  Condizione da valutare.  Per ulteriori informazioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Attributo facoltativo.  Può contenere uno dei seguenti valori:<br /><br /> -   **WarnAndContinue** o **true**.  Quando un'attività non riesce, le attività successive nell'elemento [Destinazione](../msbuild/target-element-msbuild.md) e nella compilazione continua a eseguire e tutti gli errori dall'attività vengono trattati come avvisi.<br />-   **ErrorAndContinue**.  Quando un'attività non riesce, le attività successive nell'elemento `Target` e nella compilazione continua a eseguire e tutti gli errori dall'attività sono considerati come errori.<br />-   **ErrorAndStop** o **false** \(impostazione predefinita\).  Quando un'attività non riesce, le attività rimanenti nell'elemento `Target` e nella compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione viene considerato dell'errata esecuzione.<br /><br /> Le versioni di .NET Framework precedente alla 4,5 supportano i valori `false` e solo `true`.<br /><br /> Per ulteriori informazioni, vedere [How to: Ignore Errors in Tasks](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Obbligatorio se la classe dell'attività contiene una o più proprietà contrassegnate con l'attributo `[Required]`.<br /><br /> Parametro dell'attività definito dall'utente che contiene come valore quello del parametro.  Nell'elemento `Task` può essere presente un numero qualsiasi di parametri. Ciascun attributo di tale elemento corrisponde a una proprietà .NET nella classe dell'attività.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Output](../msbuild/output-element-msbuild.md)|Archivia gli output dell'attività nel file di progetto.  In un'attività possono essere presenti zero o più elementi `Output`.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Destinazione](../msbuild/target-element-msbuild.md)|Elemento contenitore per le attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Note  
 Un elemento `Task` in un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] crea un'istanza di un'attività, ne imposta le proprietà e la esegue.  L'elemento `Output` archivia i parametri di output nelle proprietà o negli elementi da utilizzare in altri punti del file di progetto.  
  
 Se sono presenti elementi [OnError](../msbuild/onerror-element-msbuild.md) nell'elemento `Target` padre di un'attività, questi verranno comunque valutati se l'attività ha esito negativo e il valore di `ContinueOnError` è impostato su `false`.  Per ulteriori informazioni sulle attività, vedere [Tasks](../msbuild/msbuild-tasks.md).  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene creata un'istanza della classe dell'[attività Csc](../msbuild/csc-task.md), vengono impostate sei proprietà e viene eseguita l'attività.  Dopo l'esecuzione, il valore della proprietà `OutputAssembly` dell'oggetto viene inserito in un elenco di elementi denominato `FinalAssemblyName`.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)