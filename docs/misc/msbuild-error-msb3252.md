---
title: "Errore MSB3252 di MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB3252"
helpviewer_keywords: 
  - "MSB3252"
ms.assetid: 4e6982b8-84b3-4d21-94e1-05cc10bf1393
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Errore MSB3252 di MSBuild
**MSB3252: il progetto include un riferimento all'assembly \<nome\>,  che non fa parte di .NET Framework Client Profile.  In mancanza di questo riferimento, possono verificarsi errori di compilazione o di runtime.**  
  
 È stata eseguita una chiamata a un membro di un assembly, o assembly dipendente, che non fa parte di [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Pertanto, la chiamata non può essere risolta e l'applicazione non può essere compilata.  
  
 Per ulteriori informazioni su [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], vedere [Profilo client .NET Framework](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Per correggere l'errore  
  
-   Rimuovere dal progetto il riferimento all'assembly specificato o scegliere come destinazione la versione completa di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anziché il sottoinsieme [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] della libreria.  Per informazioni su come destinare l'applicazione alla versione completa di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], vedere [Procedura: destinare una versione di .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Vedere anche  
 [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)