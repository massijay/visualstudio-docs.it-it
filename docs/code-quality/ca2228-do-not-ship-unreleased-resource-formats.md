---
title: "CA2228: Non fornire formati di risorse non rilasciati | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotShipUnreleasedResourceFormats"
  - "CA2228"
helpviewer_keywords: 
  - "CA2228"
  - "DoNotShipUnreleasedResourceFormats"
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2228: Non fornire formati di risorse non rilasciati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 È stato compilato un file di risorse utilizzando una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] attualmente non supportata.  
  
## Descrizione della regola  
 I file di risorse compilati utilizzando versioni preliminari di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] potrebbero non essere utilizzabili dalle versioni supportate di .NET Framework.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, compilare la risorsa utilizzando una versione supportata di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.