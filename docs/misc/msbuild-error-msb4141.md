---
title: "Errore MSB4141 di MSBuild | Microsoft Docs"
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
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Errore MSB4141 di MSBuild
**MSB4141: il valore MSBuildToolsPath non è specificato per il parametro ToolsVersion "\<x.x\>".**  
  
 È stato definito un set di strumenti personalizzato ma nessun valore è stato specificato per `MSBuildToolsPath`.  
  
### Per correggere l'errore  
  
-   Specificare un valore valido per `MSBuildToolsPath` quando si definisce un set di strumenti personalizzato nel Registro di sistema o nel file di configurazione [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Vedere anche  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)