---
title: "Procedura: utilizzare caratteri di escape speciali in MSBuild | Microsoft Docs"
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
  - "caratteri speciali, escape"
  - "caratteri di escape"
  - "caratteri di escape"
  - "MSBuild, escape dei caratteri speciali"
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: utilizzare caratteri di escape speciali in MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alcuni caratteri hanno un significato speciale [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] i file di progetto. Esempi di caratteri includono un punto e virgola (;) e l'asterisco (*). Per un elenco completo di questi caratteri speciali, vedere [caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Per utilizzare questi caratteri speciali come valori letterali in un file di progetto, deve essere specificate utilizzando la sintassi %*xx*, dove *xx* rappresenta il valore ASCII esadecimale del carattere.  
  
## <a name="msbuild-special-characters"></a>Caratteri speciali di MSBuild  
 Un esempio in cui vengono utilizzati caratteri speciali sono il `Include` attributo degli elenchi di elementi. Ad esempio, l'elenco di elementi seguente dichiara due elementi: `MyFile.cs` e `MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Se si desidera dichiarare un elemento che contiene un punto e virgola nel nome, è necessario utilizzare %*xx* sintassi per ignorare il punto e virgola ed evitare che [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di dichiarare due elementi distinti. Ad esempio, l'elemento seguente ignora il punto e virgola e dichiara un elemento denominato `MyFile.cs;MyClass.cs`.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Per utilizzare un carattere speciale di MSBuild come carattere letterale  
  
-   Utilizzare la notazione %*xx* al posto del carattere speciale, dove *xx* rappresenta il valore esadecimale del carattere ASCII. Ad esempio, per usare un asterisco (*) come carattere letterale, usare il valore `%2A`.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild1.md)
 [elementi](../msbuild/msbuild-items.md)