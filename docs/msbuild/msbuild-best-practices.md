---
title: Procedure consigliate per MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 881075ee32ccac155237035dbe1a2f6d17a82893
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-best-practices"></a>Procedure consigliate di MSBuild
Per la scrittura degli script di MSBuild è consigliabile seguire le indicazioni riportate di seguito:  
  
-   I valori di proprietà predefiniti vengono gestiti meglio con l'attributo `Condition` e non dichiarando una proprietà il cui valore predefinito può essere sottoposto a override nella riga di comando. Ad esempio, usare  
  
     `<MyProperty Condition="'$(MyProperty)' == ''">`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evitare i caratteri jolly quando si selezionano elementi. Al contrario, specificare i file in modo esplicito. Ciò semplifica l'individuazione degli errori che possono verificarsi quando si aggiungono o si eliminano file.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md) (Concetti avanzati)
