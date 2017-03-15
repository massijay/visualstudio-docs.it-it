---
title: "MSBuild Response Files | Microsoft Docs"
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
  - "response files, MSBuild"
  - "MSBuild, response files"
  - "MSBuild, .rsp files"
  - ".rsp files"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# MSBuild Response Files
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I file di risposta \(con estensione rsp\) sono file di testo contenenti opzioni della riga di comando di MSBuild.exe.  È possibile inserire ogni opzione su una riga separata o tutte le opzioni su una stessa riga.  Le righe di commento sono precedute da un simbolo **\#**.  L'opzione **@** viene utilizzata per passare un altro file di risposta a MSBuild.exe.  
  
 Il file di risposta automatica è un file rsp speciale utilizzato automaticamente da MSBuild.exe durante la compilazione di un progetto.  Il file MSBuild.rsp deve essere contenuto nella stessa directory di MSBuild.exe, altrimenti non verrà trovato.  È possibile modificare questo file per specificare opzioni della riga di comando predefinite per MSBuild.exe.  Se ad esempio si utilizza lo stesso logger ogni volta che si compila un progetto, è possibile aggiungere l'opzione **\/logger** a MSBuild.rsp e il logger verrà utilizzato da MSBuild.exe ogni volta che verrà compilato un progetto.  
  
## Vedere anche  
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)