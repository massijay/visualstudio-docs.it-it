---
title: "Errore MSB4142 di MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Errore MSB4142 di MSBuild
**MSB4142: il valore di MSBuildToolsPath non corrisponde al valore di MSBuildBinPath per il parametro ToolsVersion "\<x.x\>".**  
  
 La definizione del set di strumenti specifica valori diversi per `MSBuildBinPath` e `MSBuildToolsPath`.  
  
### Per correggere l'errore  
  
-   Verificare che i valori per `MSBuildBinPath` e `MSBuildToolsPath` siano gli stessi nella definizione del set di strumenti.  
  
## Vedere anche  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)