---
title: "MSBuild Targets | Microsoft Docs"
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
  - "MSBuild, targets"
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Targets
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le destinazioni raggruppano le attività in un determinato ordine e consentono la scomposizione del processo di compilazione in unità più piccole.  Una destinazione, ad esempio, può eliminare tutti i file nella directory di output per preparare la compilazione, mentre un'altra può compilare gli input per il progetto ed inserirli nella directory vuota.  Per ulteriori informazioni sulle attività, vedere [Tasks](../msbuild/msbuild-tasks.md).  
  
## Dichiarazione delle destinazioni nel file di progetto  
 Per dichiarare una destinazione in un progetto si utilizza l'elemento [Target](../msbuild/target-element-msbuild.md).  Nel codice XML seguente, ad esempio, viene creata una destinazione denominata Construct, che a sua volta chiama l'attività Csc con il tipo di elemento Compile.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Analogamente alle proprietà di MSBuild, le destinazioni possono essere ridefinite.  Di seguito è riportato un esempio:  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Se si esegue AfterBuild, viene visualizzato solo "Second occurrence".  
  
## Ordine di compilazione delle destinazioni  
 Se l'input di una destinazione dipende dall'output di un'altra destinazione, le destinazioni devono essere ordinate.  È possibile specificare l'ordine di esecuzione delle destinazioni in diversi modi.  
  
-   Destinazioni iniziali  
  
-   Destinazioni predefinite  
  
-   Prima destinazione  
  
-   Dipendenze fra destinazioni  
  
-   `BeforeTargets` e `AfterTargets` \(MSBuild 4.0\)  
  
 Una destinazione non viene mai eseguita due volte durante una singola compilazione, anche se una destinazione successiva nella compilazione dipende da essa.  Quando una destinazione viene eseguita, il contributo di quest'ultima alla compilazione è completo.  
  
 Per dettagli e ulteriori informazioni sull'ordine di compilazione delle destinazioni, vedere [Ordine di compilazione delle destinazioni](../msbuild/target-build-order.md).  
  
## Divisione in batch delle destinazioni  
 Un elemento di destinazione può disporre di un attributo `Outputs` che specifica i metadati nel formato %\(metadati\).  In tal caso, MSBuild esegue la destinazione una volta per ogni valore univoco dei metadati, raggruppando, o "unendo in batch", gli elementi che hanno tale valore dei metadati.  Di seguito è riportato un esempio:  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 raggruppa in batch gli elementi Reference in base ai relativi metadati RequiredTargetFramework.  L'output della destinazione è analogo al seguente:  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
  
```  
  
 L'unione in batch delle destinazioni viene utilizzata raramente nelle compilazioni reali.  È più comune l'unione in batch delle attività.  Per ulteriori informazioni, vedere [Batching](../msbuild/msbuild-batching.md).  
  
## Compilazioni incrementali  
 Le compilazioni incrementali sono compilazioni ottimizzate in modo che le destinazioni con file di output aggiornati rispetto ai relativi file di input corrispondenti non vengano eseguite.  Un elemento di destinazione può disporre sia di un attributo `Inputs`, che indica gli elementi che la destinazione accetta come input, che di un attributo `Outputs`, che indica gli elementi che produce come output.  
  
 Se tutti gli elementi di output sono aggiornati, MSBuild ignora la destinazione, con un conseguente significativo miglioramento della velocità di compilazione.  Questo processo è detto compilazione incrementale della destinazione.  Se solo alcuni file sono aggiornati, MSBuild esegue la destinazione senza gli elementi aggiornati.  Questo processo è detto compilazione incrementale parziale della destinazione.  Per ulteriori informazioni, vedere [Incremental Builds](../msbuild/incremental-builds.md).  
  
## Vedere anche  
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)   
 [How to: Use the Same Target in Multiple Project Files](../Topic/How%20to:%20Use%20the%20Same%20Target%20in%20Multiple%20Project%20Files.md)