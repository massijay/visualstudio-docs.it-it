---
title: Risoluzione dei problemi di analisi di codice | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>Risoluzione dei problemi di analisi codice
In questo argomento contiene informazioni sulla risoluzione dei problemi per i seguenti problemi di analisi codice di Visual Studio.  
  
-   [Modifiche in un Visual Studio 2010 regola Set non riflesse nelle versioni precedenti di Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Modifiche in un Visual Studio 2010 regola Set non riflesse nelle versioni precedenti di Visual Studio  
 Quando si crea una set di regole in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] che contiene un set di regole figlio, una modifica al set di regole figlio potrebbe non essere applicata nelle esecuzioni dell'analisi del codice nei computer che utilizzano una versione precedente di Visual Studio. Per risolvere questo problema, è necessario forzare una riscrittura del set di regole padre, ovvero il set di regole che contiene il set di regole figlio.  
  
1.  Aprire il padre del set di regole [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Apportare una modifica, ad esempio aggiunta o rimozione di una regola e quindi salvare il set di regole.  
  
3.  Riaprire il set di regole, annullare la modifica e quindi salvare il nuovo set di regole.  
  
## <a name="see-also"></a>Vedere anche  
 [Analisi della qualità dell'applicazione](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Uso di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)