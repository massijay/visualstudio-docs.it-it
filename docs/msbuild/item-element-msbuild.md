---
title: "Elemento Item (MSBuild) | Microsoft Docs"
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
  - "Item (elemento) [MSBuild]"
  - "Elemento < item > [MSBuild]"
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 31
caps.handback.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento Item (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene un elemento definito dall'utente e i relativi metadati. Ogni elemento usato in un progetto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] deve essere specificato come elemento figlio di un elemento `ItemGroup`.  
  
 \< progetto>  
 \< ItemGroup>  
 \< elemento>  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Include`|Attributo obbligatorio.<br /><br /> Il file o carattere jolly da includere nell'elenco di elementi.|  
|`Exclude`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da escludere dall'elenco di elementi.|  
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Per ulteriori informazioni, vedere [condizioni](../msbuild/msbuild-conditions.md).|  
|`Remove`|Attributo facoltativo.<br /><br /> Il file o carattere jolly da eliminare dall'elenco di elementi.<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
|`KeepMetadata`|Attributo facoltativo.<br /><br /> I metadati per gli elementi di origine da aggiungere agli elementi di destinazione. Solo i metadati i cui nomi vengono specificati nell'elenco delimitato da punto e virgola vengono trasferiti da un elemento di origine a un elemento di destinazione. Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
|`RemoveMetadata`|Attributo facoltativo.<br /><br /> I metadati per gli elementi di origine da non trasferire agli elementi di destinazione. Tutti i metadati vengono trasferiti da un elemento di origine a un elemento di destinazione, ad eccezione dei metadati i cui nomi sono contenuti nell'elenco di nomi separati da punto e virgola. Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
|`KeepDuplicates`|Attributo facoltativo.<br /><br /> Specifica se un elemento deve essere aggiunto al gruppo di destinazione se è un duplicato esatto di un elemento esistente. Se l'elemento di origine e destinazione hanno lo stesso valore `Include`, ma metadati diversi, l'elemento viene aggiunto anche se `KeepDuplicates` è impostato su `false`. Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).<br /><br /> Questo attributo è valido solo se è stato specificato per un elemento in un `ItemGroup` che si trova in un `Target`.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Chiave dei metadati di elemento definita dall'utente che contiene il valore dei metadati dell'elemento. Possono esistere zero o più elementi `ItemMetadata` in un elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento di raggruppamento per elementi.|  
  
## <a name="remarks"></a>Note  
 Gli elementi `Item` definiscono gli input nel sistema di compilazione e vengono raggruppati in raccolte di elementi in base ai relativi nomi definiti dall'utente. Questi insiemi di elementi possono essere utilizzati come parametri per [attività](../msbuild/msbuild-tasks.md), che utilizzano i singoli elementi nelle raccolte per eseguire i passaggi del processo di compilazione. Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).  
  
 Utilizzando la notazione `@(`*myType*`)` consente una raccolta di elementi di tipo *myType* essere espanso in un elenco delimitato da punto e virgola di stringhe e passato a un parametro. Se il parametro è di tipo `string`, il valore del parametro è l'elenco di elementi, separati da punti e virgola. Se il parametro è una matrice di stringhe (`string[]`), ogni elemento viene inserito nella matrice in base alla posizione dei punti e virgola. Se il parametro dell'attività è di tipo <xref:Microsoft.Build.Framework.ITaskItem>`[]`, il valore è il contenuto della raccolta di elementi con eventuali metadati associati. Per delimitare ciascun elemento utilizzando un carattere diverso da un punto e virgola, utilizzare la sintassi `@(`*myType*`, '`*separatore*`')`.  
  
 Il [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] motore può valutare caratteri jolly, ad esempio `*` e `?` e i caratteri jolly ricorsivi, ad esempio `/**/*.cs`. Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene illustrato come dichiarare due elementi di tipo `CSFile`. Il secondo elemento dichiarato contiene i metadati con `MyMetadata` impostato su `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi](../msbuild/msbuild-items.md)   
 [Proprietà di MSBuild](../msbuild/msbuild-properties.md)   
 [Riferimenti dello Schema di File di progetto](../msbuild/msbuild-project-file-schema-reference.md)