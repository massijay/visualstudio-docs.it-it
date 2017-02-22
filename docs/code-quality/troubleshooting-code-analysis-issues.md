---
title: "Risoluzione dei problemi di analisi codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
caps.handback.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Risoluzione dei problemi di analisi codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono fornite informazioni sulla risoluzione dei problemi relativi all'analisi codice di Visual Studio riportati di seguito.  
  
-   [Modifiche in un set di regole di Visual Studio 2010 non riflesse nelle versioni precedenti di Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Modifiche in un set di regole di Visual Studio 2010 non riflesse nelle versioni precedenti di Visual Studio  
 Quando si crea un set di regole in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] che contiene un set di regole figlio, è possibile che una modifica al set di regole figlio non venga applicata nelle esecuzioni dell'analisi codice su computer che utilizzano una versione precedente di Visual Studio.  Per risolvere questo problema, è necessario forzare una riscrittura del set di regole padre, ovvero il set di regole che contiene il set di regole figlio.  
  
1.  Aprire il set di regole padre in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Apportare una modifica, ad esempio l'aggiunta o la rimozione di una regola, quindi salvare il set di regole.  
  
3.  Riaprire il set di regole, invertire la modifica, quindi salvare nuovamente il set di regole.  
  
## Vedere anche  
 [Analisi della qualità delle applicazioni](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilizzo di set di regole per raggruppare regole di analisi del codice](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)