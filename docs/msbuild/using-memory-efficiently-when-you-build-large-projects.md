---
title: "Using Memory Efficiently When You Build Large Projects | Microsoft Docs"
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
  - "memory use (MSBuild)"
  - "msbuild, efficient memory use building large trees"
  - "caching (MSBuild)"
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Using Memory Efficiently When You Build Large Projects
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nei progetti di grandi dimensioni sono spesso contenuti molti sottoprogetti e altre dipendenze che possono utilizzare molta memoria di sistema durante la compilazione.  Quando la memoria di sistema disponibile è ridotta, anche le prestazioni del sistema possono risultare inferiori.  Le versioni precedenti dei progetti di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rimangono in memoria o, nella versione 3.5 i progetti vengono rimossi ma vengono conservati nella cache i risultati della compilazione per poterli recuperare successivamente.  
  
 Nella versione 4.0 questo tipo di gestione della memoria avviene automaticamente e non è necessario utilizzare proprietà come `UnloadProjectsOnCompletion` e `UseResultsCache` nei progetti.  
  
## Vedere anche  
 [Building Multiple Projects in Parallel](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)