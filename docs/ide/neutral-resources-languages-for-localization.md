---
title: "Linguaggi di risorse non associate ad alcun paese per la localizzazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "impostazioni cultura, individuazione di risorse"
  - "globalizzazione [Visual Studio], risorse"
  - "localizzazione [Visual Studio], risorse"
  - "risorse neutre"
  - "NeutralResourcesLanguageAttribute (classe)"
  - "risorse [Visual Studio], sistema di fallback"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Linguaggi di risorse non associate ad alcun paese per la localizzazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La classe <xref:System.Resources.NeutralResourcesLanguageAttribute> specifica le impostazioni cultura delle risorse incluse nell'assembly principale.  Questo attributo viene utilizzato per migliorare le prestazioni facendo in modo che l'oggetto <xref:System.Resources.ResourceManager> non cerchi le risorse incluse nell'assembly principale.  
  
 Nel codice riportato di seguito viene illustrato come impostare il linguaggio di risorse non associate ad alcun paese.  Il codice può essere inserito in uno script di compilazione oppure nel file AssemblyInfo.vb o AssemblyInfo.cs.  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## Vedere anche  
 <xref:System.Resources.ResourceManager>   
 [Introduzione alle applicazioni internazionali basate su .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Organizzazione gerarchica di risorse per la localizzazione](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Localizzazione di applicazioni](../ide/localizing-applications.md)   
 [Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)