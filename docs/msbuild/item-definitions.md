---
title: "Item Definitions | Microsoft Docs"
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
  - "msbuild, item definitions"
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Item Definitions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 2.0 consente la dichiarazione statica di elementi nei file di progetto utilizzando l'elemento [ItemGroup](../msbuild/itemgroup-element-msbuild.md).  I metadati possono essere tuttavia aggiunti solo al livello dell'elemento, anche se sono identici per tutti gli elementi.  A partire da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, viene introdotto un elemento di progetto denominato [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) che consente di superare questa limitazione.  *ItemDefinitionGroup* consente di definire un set di definizioni degli elementi che aggiungono i valori dei metadati predefiniti a tutti gli elementi del tipo dell'elemento denominato.  
  
 L'elemento *ItemDefinitionGroup* viene visualizzato immediatamente dopo l'elemento [Project](../msbuild/project-element-msbuild.md) nel file di progetto.  Le definizioni di elementi offrono le funzionalità seguenti:  
  
-   È possibile definire i metadati predefiniti globali per gli elementi fuori di una destinazione.  Ovvero, gli stessi metadati si applicano a tutti gli elementi del tipo specificato.  
  
-   I tipi di elemento possono presentare più definizioni.  Quando le specifiche aggiuntive dei metadati vengono aggiunte al tipo, l'ultima specifica ha la precedenza. I metadati seguono lo stesso ordine di importazione delle proprietà che seguono.  
  
-   I metadati possono essere additivi.  Ad esempio, i valori CDefines vengono accumulati in modo condizionale, a seconda delle proprietà impostate.  Ad esempio `MT;STD_CALL;DEBUG;UNICODE`.  
  
-   I metadati possono essere rimossi.  
  
-   Le condizioni possono essere utilizzate per controllare l'inclusione di metadati.  
  
## Valori predefiniti dei metadati degli elementi  
 I metadati degli elemento definiti in un ItemDefinitionGroup sono solo una dichiarazione di metadati predefiniti.  I metadati non vengono applicati a meno che non venga definito un elemento che utilizza un ItemGroup che contenga i valori dei metadati.  
  
> [!NOTE]
>  In molti degli esempi in questo argomento, viene illustrato un elemento ItemDefinitionGroup, ma la definizione di ItemGroup corrispondente viene omessa per chiarezza.  
  
 I metadati definiti in modo esplicito in un ItemGroup hanno la precedenza sui metadati in ItemDefinitionGroup.  I metadati in ItemDefinitionGroup vengono applicati solo per i metadati non definiti in un ItemGroup.  Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>        
</ItemDefinitionGroup>  
<ItemGroup>  
    <i Include="a">  
        <o>o1</o>  
        <n>n2</n>  
    </i>  
</ItemGroup>  
```  
  
 In questo esempio, i metadati predefiniti "m" sono applicati all'elemento "i" perché non sono definiti in modo esplicito dall'elemento "i".  I metadati predefiniti "n", invece, non sono applicati all'elemento "i" perché sono già definiti dall'elemento "i".  
  
> [!NOTE]
>  I nomi di parametri ed elementi XML prevedono la distinzione tra maiuscole e minuscole.  I metadati degli elementi e i nomi di proprietà ed elementi non prevedono la distinzione tra maiuscole e minuscole.  Pertanto, gli elementi ItemDefinitionGroup i cui nomi differiscono solo per l'uso delle maiuscole o delle minuscole devono essere considerati come lo stesso ItemGroup.  
  
## Origini dei valori  
 I valori per i metadati definiti in un ItemDefinitionGroup possono provenire da molte origini diverse, come segue:  
  
-   Proprietà PropertyGroup  
  
-   Elemento da un ItemDefinitionGroup  
  
-   Trasformazione dell'elemento su un elemento ItemDefinitionGroup  
  
-   Variabile di ambiente  
  
-   Proprietà globale \(dalla riga di comando di MSBuild.exe\)  
  
-   Proprietà riservata  
  
-   Metadati noti in un elemento da un ItemDefinitionGroup  
  
-   Sezione CDATA \<\!\[CDATA\[nessun dato analizzato\]\]\>  
  
> [!NOTE]
>  I metadati dell'elemento da un ItemGroup non sono utili in una dichiarazione di metadati ItemDefinitionGroup perché gli elementi ItemDefinitionGroup vengono elaborati prima degli elementi ItemGroup.  
  
## Definizioni additive e multiple  
 Quando si aggiungono definizioni o si utilizzano più ItemDefinitionGroups, tenere presente quanto segue:  
  
-   La specifica dei metadati aggiuntivi viene aggiunta al tipo.  
  
-   L'ultima specifica ha la precedenza.  
  
 In presenza di più ItemDefinitionGroup, ogni specifica successiva aggiunge i propri metadati alla definizione precedente.  Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <n>n1</n>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <o>o1</o>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 In questo esempio, i metadati "o" vengono aggiunti a "m" e "n".  
  
 È possibile aggiungere, inoltre, i valori dei metadati definiti in precedenza.  Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
 In questo esempio, il valore definito in precedenza per i metadati "m" \(m1\) viene aggiunto al nuovo valore \(m2\), in modo che il valore finale sia "m1;m2".  
  
> [!NOTE]
>  Ciò si verifica anche nello stesso ItemDefinitionGroup.  
  
 Quando si esegue l'override dei metadati definiti in precedenza, l'ultima specifica ha la precedenza.  Nell'esempio riportato di seguito, il valore finale dei metadati "m" è compreso tra "m1" e "m1a".  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m>m1a</m>  
    </i>  
</ItemDefinitionGroup>    
```  
  
## Utilizzo delle condizioni in un ItemDefinitionGroup  
 È possibile utilizzare condizioni in un ItemDefinitionGroup per controllare l'inclusione di metadati.  Ad esempio:  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 In questo caso, i metadati predefiniti "m1" sull'elemento "i" vengono inclusi solo se il valore della proprietà "Configuration" è "Debug".  
  
> [!NOTE]
>  Solo i riferimenti dei metadati locali sono supportati nelle condizioni.  
  
 I riferimenti ai metadati definiti in un ItemDefinitionGroup precedente sono locali per l'elemento, non per il gruppo di definizione.  Ovvero, l'ambito dei riferimenti è specifico dell'elemento.  Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Nell'esempio, l'elemento "i" fa riferimento all'elemento "test" nella condizione.  
  
## Override ed eliminazione di metadati  
 L'override di metadati definiti in un elemento ItemDefinitionGroup può essere eseguito in un elemento ItemDefinitionGroup successivo lasciando vuoto il valore dei metadati.  Se si lascia vuoto il valore di un elemento dei metadati è anche possibile eliminarli.  Ad esempio:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
<ItemDefinitionGroup>  
    <i>  
        <m></m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 L'elemento "i" contiene ancora i metadati "m", ma il valore è ora vuoto.  
  
## Ambito dei metadati  
 L'ambito di ItemDefinitionGroups è globale su proprietà definite e globali ovunque siano definite.  Le definizioni dei metadati predefinite in un ItemDefinitionGroup possono essere autoreferenziali.  Ad esempio, di seguito viene utilizzato un semplice riferimento ai metadati:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 È possibile utilizzare anche un riferimento ai metadati qualificato:  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Quanto segue pertanto non è valido:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Iniziando in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, ItemGroups può essere anche autoreferenziale.  Ad esempio:  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## Vedere anche  
 [Batching](../msbuild/msbuild-batching.md)