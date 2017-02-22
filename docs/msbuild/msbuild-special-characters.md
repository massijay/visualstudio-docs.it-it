---
title: "MSBuild Special Characters | Microsoft Docs"
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
  - "escape characters"
  - "escape"
  - "MSBuild Escape Characters"
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Special Characters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] riserva alcuni caratteri per utilizzo speciale in contesti specifici.  È necessario utilizzare caratteri di escape solo per tali caratteri se si desidera utilizzarli in modo letterale nel contesto nel quale sono riservati.  Un asterisco, ad esempio, ha significato speciale solo negli attributi `Include` e `Exclude` di una definizione dell'elemento e nelle chiamate a `CreateItem`.  Se si desidera che un asterisco venga visualizzato come asterisco in uno di tali contesti, è necessario ricorrere ai relativi caratteri di escape.  In ogni altro contesto, è sufficiente digitare l'asterisco dove si desidera che venga visualizzato.  
  
 Per utilizzare un carattere di escape per un carattere speciale, utilizzare la sintassi %*xx*, dove *xx* rappresenta il valore ASCII esadecimale del carattere.  Per ulteriori informazioni, vedere [How to: Escape Special Characters in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## Caratteri speciali  
 Nella tabella seguente sono elencati i caratteri speciali di [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:  
  
|**Carattere**|**ASCII**|**Utilizzo riservato**|  
|-------------------|---------------|----------------------------|  
|%|%25|Riferimento ai metadati|  
|$|%24|Riferimento a proprietà|  
|@|%40|Riferimento agli elenchi di elementi|  
|'|%27|Condizioni e altre espressioni|  
|;|%3B|Separatore di elenco|  
|?|%3F|Carattere jolly per nomi di file negli attributi `Include` e `Exclude`|  
|\*|%2A|Carattere jolly per nomi di file negli attributi `Include` e `Exclude`|  
  
## Vedere anche  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)   
 [Items](../msbuild/msbuild-items.md)