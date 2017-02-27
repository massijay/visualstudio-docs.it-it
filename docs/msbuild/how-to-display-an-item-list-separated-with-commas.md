---
title: "How to: Display an Item List Separated with Commas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, separating items with semicolons"
  - "MSBuild, formatting item collections"
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# How to: Display an Item List Separated with Commas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si utilizzano elenchi di elementi in [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\), può risultare utile visualizzarne i contenuti in modo da agevolare la lettura.  Potrebbe inoltre essere presente un'attività che dispone di un elenco di elementi separati da una speciale stringa di separazione.  In entrambi i casi, per tali elenchi è possibile specificare una stringa di separazione.  
  
## Separazione degli elementi di un elenco con virgole  
 Per impostazione predefinita, in [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vengono utilizzati punti e virgola per separare gli elementi in un elenco.  Si consideri, ad esempio, un elemento `Message` con il valore seguente:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Se l'elenco di elementi `@(TXTFile)` contiene gli elementi App1.txt, App2.txt e App3.txt, il messaggio sarà:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Se si desidera modificare il comportamento predefinito, è possibile specificare un separatore personalizzato.  La sintassi utilizzata per specificare il separatore di un elenco di elementi è la seguente:  
  
 `@(ItemListName, '<separator>')`  
  
 Il separatore può essere un unico carattere o una stringa e deve essere racchiuso tra virgolette singole.  
  
#### Per inserire una virgola e uno spazio tra gli elementi  
  
-   Utilizzare una notazione di elemento simile alla seguente:  
  
     `@(TXTFile, ', ')`  
  
## Esempio  
 In questo esempio, l'attività [Exec](../msbuild/exec-task.md) esegue lo strumento findstr per trovare stringhe di testo specificate nel file Phrases.txt.  Nel comando findstr le stringhe di ricerca letterali vengono indicate dall'opzione **\/c:**, pertanto il separatore di elementi `/c:` viene inserito tra gli elementi nell'elenco di elementi `@(Phrase)`.  
  
 In questo caso il comando della riga di comando equivalente è il seguente:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Items](../msbuild/msbuild-items.md)