---
title: 'CA2228: Non fornire formati di risorse non rilasciati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 959d88751ff250e54f6a3f89f0b4b0554add96d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Non fornire formati di risorse non rilasciati
|||  
|-|-|  
|TypeName|DoNotShipUnreleasedResourceFormats|  
|CheckId|CA2228|  
|Categoria|Microsoft. Usage|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
 Un file di risorse è stato creato utilizzando una versione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che non è attualmente supportato.  
  
## <a name="rule-description"></a>Descrizione della regola  
 File di risorse compilati utilizzando versioni non definitive del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] potrebbe non essere utilizzabili dalle versioni supportate di .NET Framework.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, compilare la risorsa utilizzando una versione supportata del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.