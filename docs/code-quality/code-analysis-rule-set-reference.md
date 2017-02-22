---
title: "Tabella di riferimento del set di regole di analisi del codice | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analisi codice, set di regole"
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 43
caps.handback.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tabella di riferimento del set di regole di analisi del codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si configura l'analisi del codice per i progetti in codice gestito in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], viene visualizzato un elenco di *set di regole* predefiniti.  È possibile utilizzare uno dei set di regole standard o personalizzare un set di regole per soddisfare i requisiti del progetto.  
  
## Set di regole disponibili  
 Nella tabella seguente sono elencati i set di regole predefiniti:  
  
|||  
|-|-|  
|[Set di regole Tutte le regole](../code-quality/all-rules-rule-set.md)|Questo set di regole contiene tutte le regole.  L'esecuzione del set di regole potrebbe causare la segnalazione di un numero elevato di avvisi.  Utilizzare questo set di regole per ottenere una panoramica di tutti i problemi rilevati nel codice.  Tali informazioni sono utili per scegliere il set di regole specifico più appropriato per i progetti.|  
|[Set di regole base di correttezza per codice gestito](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Queste regole sono orientate alla segnalazione degli errori di logica e di altri errori comuni di utilizzo delle API del framework.  Includere questo set di regole per espandere l'elenco degli avvisi segnalati dalle regole minime consigliate.|  
|[Set di regole Regole base delle linee guida di progettazione per codice gestito](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Queste regole sono orientate all'applicazione delle procedure consigliate per la scrittura di codice semplice da comprendere e da utilizzare.  Includere questo set di regole se il progetto contiene codice di libreria o se si desidera applicare le procedure consigliate per la scrittura di codice di facile manutenzione.|  
|[Set di regole estese di correttezza per codice gestito](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Queste regole espandono le regole base di correttezza per segnalare il numero più elevato possibile degli errori di logica e di utilizzo del framework.  Particolare attenzione è rivolta a scenari specifici quali l'interoperabilità COM e le applicazioni mobili.  Includere questo set di regole se tali scenari hanno rilevanza per il progetto oppure per individuare ulteriori problemi nel progetto.|  
|[Set di regole Regole estese delle linee guida di progettazione per codice gestito](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Queste regole espandono le regole base delle linee guida di progettazione per segnalare il numero più elevato possibile degli errori di usabilità e di manutenibilità.  Viene posta particolare attenzione sulle linee guida di denominazione.  Includere questo set di regole se il progetto contiene codice di libreria o se si desidera applicare gli standard ottimali per la scrittura di codice di facile manutenzione.|  
|[Set di regole delle Regole di globalizzazione per codice gestito](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Queste regole sono orientate alla segnalazione dei problemi di visualizzazione dei dati nell'applicazione quando questa viene utilizzata con impostazioni di lingua, locali e cultura diverse.  Includere questo set di regole se l'applicazione è localizzata o globalizzata.|  
|[Set di regole minime gestite per codice gestito](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Queste regole sono incentrate sui problemi critici del codice per i quali l'analisi codice è più accurata.  Il numero di regole disponibili è esiguo e sono progettate per essere eseguite solo in alcune edizioni di Visual Studio.  Utilizzare MinimumRecommendedRules.ruleset con altre edizioni di Visual Studio.|  
|[Set di regole consigliate gestite per codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Queste regole sono orientate alla segnalazione dei problemi critici del codice, quali problemi di sicurezza, arresti anomali dell'applicazione e altri errori di logica e di progettazione rilevanti.  È necessario includere questo set di regole nei set di regole personalizzati creati per i progetti.|  
|[Set di regole minime miste](../code-quality/mixed-minimum-rules-rule-set.md)|Queste regole sono orientate ai problemi più critici dei progetti C\+\+ che supportano Common Language Runtime, inclusi i problemi di sicurezza potenziali e gli arresti anomali delle applicazioni.  È necessario includere questo set di regole in ogni set di regole personalizzato, creato per i progetti C\+\+ che supportano Common Language Runtime.|  
|[Set di regole consigliate miste](../code-quality/mixed-recommended-rules-rule-set.md)|Queste regole sono incentrate sui problemi più comuni e quelli critici dei progetti C\+\+ che supportano Common Language Runtime, incluse potenziali lacune della sicurezza, arresti anomali delle applicazioni e altri errori importanti relativi a logica e progettazione.  È necessario includere questo set di regole in ogni set di regole personalizzato, creato per i progetti C\+\+ che supportano Common Language Runtime.  Questo set di regole è progettato per essere configurato con l'edizione di Visual Studio Professional e superiori.|  
|[Set di regole minime native](../code-quality/native-minimum-rules-rule-set.md)|Queste regole sono orientate ai problemi più critici del codice nativo, inclusi i problemi di sicurezza potenziali e gli arresti anomali delle applicazioni.  È necessario includere questo set di regole in ogni set di regole personalizzato, creato per i progetti nativi.|  
|[Set di regole consigliate native](../code-quality/native-recommended-rules-rule-set.md)|Queste regole sono incentrate sui problemi più critici e comuni nel codice nativo, incluse eventuali lacune della sicurezza e arresti anomali delle applicazioni.  È necessario includere questo set di regole in ogni set di regole personalizzato, creato per i progetti nativi.  Questo set di regole è progettato per funzionare con l'edizione di Visual Studio Professional e superiori.|  
|[Set di regole di sicurezza per codice gestito](../code-quality/security-rules-rule-set-for-managed-code.md)|Questo set di regole contiene tutte le regole di sicurezza Microsoft.  Includere questo set di regole per segnalare il numero più elevato possibile di problemi potenziali della sicurezza.|