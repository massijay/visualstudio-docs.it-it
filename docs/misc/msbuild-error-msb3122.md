---
title: "MSBuild Error MSB3122 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationsApplicationNotFullTrust"
helpviewer_keywords: 
  - "MSB3122"
ms.assetid: 523e4160-f165-437a-9f19-fb2ec77d46f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3122
**MSB3122: per utilizzare l'associazione di file è necessaria l'attendibilità totale.**  
  
 La pubblicazione di un'applicazione che configura associazioni di file richiede che l'applicazione sia completamente attendibile.  
  
### Per correggere l'errore  
  
-   Attivare le impostazioni di sicurezza ClickOnce e impostare l'applicazione su un'applicazione completamente attendibile.  Per ulteriori informazioni, vedere [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md).  
  
## Vedere anche  
 [Pagina Pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)