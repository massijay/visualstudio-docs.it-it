---
title: "ItemMetadata Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "ItemMetadata Element [MSBuild]"
  - "<ItemMetadata> Element [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# ItemMetadata Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene la chiave dei metadati dell'elemento definita dall'utente che contiene il valore di metadati dell'elemento.  Un elemento può avere un numero qualsiasi di coppie chiave\-valore di metadati.  
  
## Sintassi  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Condition`|Attributo facoltativo.<br /><br /> Condizione da valutare.  Per ulteriori informazioni, vedere [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento](../msbuild/item-element-msbuild.md)|Elemento definito dall'utente che specifica gli input per il processo di compilazione.|  
  
## Valore di testo  
 Il valore di testo è facoltativo.  
  
 Questo testo specifica il valore di metadati dell'elemento, che può essere in formato testo o XML.  
  
## Note  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come aggiungere i metadati `Culture` con valore `fr` all'elemento `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## Vedere anche  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)