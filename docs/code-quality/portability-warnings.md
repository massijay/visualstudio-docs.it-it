---
title: "Avvisi di portabilit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "avvisi di portabilità"
  - "avvisi dell'analisi codice gestito, portabilità"
  - "avvisi, portabilità"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Avvisi di portabilit&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di portabilità supportano la portabilità tra sistemi operativi diversi.  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1900: I campi dei tipi di valore devono essere portabili](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Questa regola consente di verificare che le strutture dichiarate utilizzando un attributo di layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito nei sistemi operativi a 64 bit.|  
|[CA1901: Le dichiarazioni P\/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|La regola valuta la dimensione di ciascun parametro e il valore restituito di P\/Invoke e verifica che la relativa dimensione sia corretta quando viene eseguito il marshalling a codice non gestito in sistemi operativi a 32 e a 64 bit.|  
|[CA1903: Utilizzare solo API della versione di .NET Framework di destinazione](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membro o un tipo sta utilizzando un membro o un tipo introdotto in un service pack non incluso con la versione di .NET Framework di destinazione del progetto.|