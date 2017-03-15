---
title: "Errore MSB4140 di MSBuild | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Errore MSB4140 di MSBuild
**MSB4140: versione strumenti predefinita non specificata nel Registro di sistema e nel file di configurazione.**  
  
 Nel progetto non è specificato un valore predefinito `ToolsVersion`.  Pertanto, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] non è in grado di riconoscere il valore da utilizzare.  
  
### Per correggere l'errore  
  
-   Verificare che un valore `DefaultToolsVersion` sia specificato nel Registro di sistema dove sono definiti i set di strumenti, o in un file di configurazione, ad esempio msbuild.exe.config.  
  
## Vedere anche  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)