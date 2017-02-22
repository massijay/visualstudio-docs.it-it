---
title: "CPPClean Task | Microsoft Docs"
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
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), CPPClean task"
  - "CPPClean task (MSBuild (Visual C++))"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CPPClean Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elimina i file temporanei che MSBuild crea quando un progetto Visual C\+\+ è compilato.  Il processo dell'eliminazione dei file di compilazione è noto come *pulitura*.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività **CPPClean** .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**DeletedFiles**|Parametro di output `ITaskItem[]` facoltativo.<br /><br /> Definisce una matrice di elementi del file di output MSBuild che può essere utilizzato ed emesso dalle attività.|  
|**DoDelete**|Parametro **Boolean** facoltativo.<br /><br /> Se `true`, pulire i file di compilazione temporanei.|  
|**FilePatternsToDeleteOnClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punti e virgola di estensioni file di file da pulire.|  
|**FilesExcludedFromClean**|Parametro `String` facoltativo.<br /><br /> Specifica un elenco delimitato da punti e virgola di file che non devono essere puliti.|  
|**FoldersToClean**|Parametro `String` obbligatorio.<br /><br /> Specifica un elenco delimitato da punti e virgola di directory da pulire.  È possibile specificare un percorso relativo o completo e il percorso può contenere il simbolo jolly \(**\***\).|  
  
## Note  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)