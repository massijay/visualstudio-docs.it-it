---
title: "Elemento Target (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Target"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Target (elemento) [MSBuild]"
  - "<Target> (elemento) [MSBuild]"
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Target (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene un insieme di attività da eseguire in sequenza in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Sintassi  
  
```  
<Target Name="Target Name"  
        Inputs="Inputs"  
        Outputs="Outputs"  
        Returns="Returns"  
        KeepDuplicateOutputs="true/false"  
        BeforeTargets="Targets"  
        AfterTargets="Targets"  
        DependsOnTargets="DependentTarget"  
        Condition="'String A' == 'String B'">  
        Label="Label">  
    <Task>... </Task>  
    <PropertyGroup>… </PropertyGroup>  
    <ItemGroup>… </ItemGroup>  
    <OnError... />  
</Target>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Attributo obbligatorio.<br /><br /> Il nome della destinazione.|  
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare.  Se tramite la condizione viene restituito `false`, il corpo della destinazione o di eventuali destinazioni impostate nell'attributo `DependsOnTargets` non verrà eseguito.  Per ulteriori informazioni sulle condizioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
|`Inputs`|Attributo facoltativo.<br /><br /> I file che costituiscono gli input in questa destinazione.  Più file sono separati da punti e virgola.  I timestamp dei file verranno confrontato con i timestamp dei file in `Outputs` per determinare se `Target` viene aggiornato.  Per ulteriori informazioni, vedere [Incremental Builds](../msbuild/incremental-builds.md), [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md) e [Transforms](../msbuild/msbuild-transforms.md).|  
|`Outputs`|Attributo facoltativo.<br /><br /> I file che costituiscono gli output in questa destinazione.  Più file sono separati da punti e virgola.  I timestamp dei file verranno confrontato con i timestamp dei file in `Inputs` per determinare se `Target` viene aggiornato.  Per ulteriori informazioni, vedere [Incremental Builds](../msbuild/incremental-builds.md), [How to: Build Incrementally](../msbuild/how-to-build-incrementally.md) e [Transforms](../msbuild/msbuild-transforms.md).|  
|`Returns`|Attributo facoltativo.<br /><br /> Set di elementi che saranno resi disponibili per le attività tramite cui viene richiamata questa destinazione, ad esempio, le attività MSBuild.  Se sono specificate più destinazioni, queste sono separate da punti e virgola.  Se i database di destinazione nel file non dispongono di attributi di `Returns`, gli attributi di output vengono invece utilizzati per questo scopo.|  
|`KeepDuplicateOutputs`|Attributo booleano facoltativo.<br /><br /> Se `true`, riferimenti allo stesso elemento restituirà di destinazione è registrato.  Per impostazione predefinita, questo attributo è `false`.|  
|`BeforeTargets`|Attributo facoltativo.<br /><br /> Elenco di nomi di destinazioni separati da punto e virgola. Una volta specificato, indica che tale destinazione deve eseguire prima che il database di destinazione o le destinazioni specificate.  In questo modo l'autore di progetto estendere un set esistente di destinazione senza modificare direttamente.  Per ulteriori informazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).|  
|`AfterTargets`|Attributo facoltativo.<br /><br /> Elenco di nomi di destinazioni separati da punto e virgola.  Una volta specificato, indica che tale destinazione deve essere eseguita dopo la destinazione o le destinazioni specificate.  In questo modo l'autore di progetto estendere un set esistente di destinazione senza modificare direttamente.  Per ulteriori informazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).|  
|`DependsOnTargets`|Attributo facoltativo.<br /><br /> Le destinazioni che devono essere eseguite prima di questa destinazione possono essere eseguite oppure si può verificare l'analisi delle dipendenze di livello principale.  Se sono specificate più destinazioni, queste sono separate da punti e virgola.|  
|`Label`|Attributo facoltativo.<br /><br /> Un identificatore che può identificare o ordinare gli elementi di sistema e utente.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|Crea ed esegue un'istanza di un'attività [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  In una destinazione possono essere presenti zero o più attività.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Contiene un insieme di elementi definiti dall'utente di `Property`.  A partire da.NET Framework 3.5, un elemento di `Target` può contenere elementi di `PropertyGroup`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Contiene un insieme di elementi definiti dall'utente di `Item`.  A partire da.NET Framework 3.5, un elemento di `Target` può contenere elementi di `ItemGroup`.  Per ulteriori informazioni, vedere [Items](../msbuild/msbuild-items.md).|  
|[OnError](../msbuild/onerror-element-msbuild.md)|Determina una o più destinazioni a eseguire se l'attributo di `ContinueOnError` è ErrorAndStop \(o `false`\) per un'attività non riuscita.  In una destinazione possono essere presenti zero o più elementi `OnError`.  Gli elementi `OnError` eventualmente presenti devono comparire per ultimi all'interno dell'elemento `Target`.<br /><br /> Per informazioni sull'attributo di `ContinueOnError`, vedere [Task Element \(MSBuild\)](../msbuild/task-element-msbuild.md).|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Progetto](../msbuild/project-element-msbuild.md)|Elemento radice obbligatorio di un file di progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Note  
 La prima destinazione da eseguire viene specificata in fase di esecuzione.  Le destinazioni possono contenere dipendenze da altre destinazioni.  Ad esempio, una destinazione per la distribuzione dipende da una destinazione per la compilazione.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] consente di eseguire le dipendenze nell'ordine in cu sono visualizzate nell'attributo `DependsOnTargets`, da sinistra a destra.  Per ulteriori informazioni, vedere [Targets](../msbuild/msbuild-targets.md).  
  
 Anche se più destinazioni contengono una dipendenza da una specifica destinazione, questa viene eseguita una sola volta durante una compilazione.  
  
 Se una destinazione viene ignorata perché tramite il relativo attributo `Condition` viene restituito `false`, può essere comunque eseguita richiamandola in una fase successiva della compilazione. A questo punto, tramite il relativo attributo `Condition` viene restituito `true`.  
  
 Prima di MSBuild 4, tramite `Target` veniva restituito qualsiasi elemento specificato nell'attributo `Outputs`.  A tal fine, è stato necessario registrare questi elementi in MSBuild nel caso in cui venissero richiesti dalle attività successivamente nella compilazione.  Poiché non esisteva un modo per indicare quali destinazioni disponevano di output richiesti dai chiamanti, tutti gli elementi di tutti gli `Outputs` in tutte le `Target` richiamate sono stati accumulati in MSBuild.  In tal modo, i problemi per le compilazioni con un gran numero di elementi di output vengono ridimensionati.  
  
 Se l'utente specifica un attributo `Returns` per ogni elemento `Target` di un progetto, vengono registrati solo gli elementi `Target` che dispongono di un attributo `Returns`.  
  
 Un elemento `Target` potrebbe contenere un attributo `Outputs` e un attributo `Returns`.  L'attributo `Outputs` viene utilizzato insieme all'attributo `Inputs` per determinare se la destinazione è aggiornata.  Tramite l'attributo `Returns`, se presente, viene eseguito l'override del valore dell'attributo `Outputs` per determinare quali elementi vengono restituiti ai chiamanti.  Se `Returns` non è presente, `Outputs` sarà reso disponibile ai chiamanti tranne nel caso descritto in precedenza.  
  
 Prima di MSBuild 4, ogni volta che in una `Target` erano inclusi più riferimenti allo stesso elemento nei relativi `Outputs`, tali elementi duplicati venivano registrati.  In compilazioni di grandi dimensioni con un numero elevato di output e numerose interdipendenze del progetto, questa situazione comporterebbe lo spreco di una notevole quantità di memoria dal momento che gli elementi duplicati non verrebbero utilizzati in alcun modo.  Quando l'attributo di `KeepDuplicateOutputs` è impostato su `true`duplicati, questi vengono registrati.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato un elemento `Target` che esegue l'attività `Csc`.  
  
```  
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">  
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
 [Targets](../msbuild/msbuild-targets.md)   
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)