---
title: "Errore MSB4135 di MSBuild | Microsoft Docs"
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
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Errore MSB4135 di MSBuild
**MSB4135: errore durante la lettura delle informazioni del set di strumenti dalla chiave del Registro di sistema "'\<chiave\>'" o da una sottochiave. '  \<key\>'**  
  
 Non è possibile leggere le informazioni del set di strumenti personalizzate definite nel Registro di sistema.  
  
### Per correggere l'errore  
  
-   Se è stato definito un set di strumenti personalizzato nel Registro di sistema, verificare che sia in formato di Registro di sistema valido, che abbia il nome `ToolsVersion` corretto e il valore `MSBuildBinPath` o `MSBuildToolsPath` corretto.  
  
## Vedere anche  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)