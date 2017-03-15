---
title: "Item Functions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, Item functions"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Item Functions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A partire da MSBuild 4.0, il codice delle attività e delle destinazioni può chiamare le funzioni dell'elemento per ottenere informazioni sugli elementi nel progetto.  Queste funzioni consentono di ottenere in modo più semplice gli elementi Distinct\(\) e sono più rapide rispetto allo scorrimento in ciclo degli elementi.  
  
## Funzioni dell'elemento della stringa  
 È possibile utilizzare i metodi e le proprietà stringa in .NET Framework per l'esecuzione su un valore dell'elemento.  Per i metodi <xref:System.String>, specificare il nome del metodo.  Per le proprietà <xref:System.String>, specificare il nome della proprietà dopo “get\_„.  
  
 Per gli elementi che dispongono di più stringhe, il metodo della stringa o esecuzioni della proprietà su ogni stringa.  
  
 Di seguito viene illustrato come utilizzare questi supporti le funzioni dell'elemento.  
  
```  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## Funzioni intrinseche dell'elemento  
 Nella tabella seguente sono elencate le funzioni intrinseche disponibili per gli elementi.  
  
|Funzione|Esempio|Descrizione|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Restituisce il numero di elementi.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Restituisce l'equivalente `Path.DirectoryName` per ogni elemento.|  
|`Distinct`|`@(MyItem->Distinct())`|Restituisce elementi da con valori distinti `Include`.  I metadati vengono ignorati.  Il confronto viene eseguito senza distinzione tra maiuscole e minuscole.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Restituisce elementi da con valori distinti `itemspec`.  I metadati vengono ignorati.  Per il confronto viene applicata la distinzione tra maiuscole e minuscole.|  
|`Reverse`|`@(MyItem->Reverse())`|Restituisce gli elementi in ordine inverso.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Restituisce `boolean` per indicare se qualsiasi elemento dispone dei metadati specificati nome e valore.  Il confronto viene eseguito senza distinzione tra maiuscole e minuscole.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Restituisce elementi da con i metadati cancellati.  Solo `itemspec` viene mantenuto.|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Restituisce gli elementi con il nome specificato di metadati.  Il confronto viene eseguito senza distinzione tra maiuscole e minuscole.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Restituisce i valori dei metadati con il nome dei metadati.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Restituisce gli elementi che dispongono dei metadati specificati nome e valore.  Il confronto viene eseguito senza distinzione tra maiuscole e minuscole.|  
  
 Di seguito viene illustrato come utilizzare l'elemento intrinseco esecuzione.  
  
```  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## Vedere anche  
 [Items](../msbuild/msbuild-items.md)