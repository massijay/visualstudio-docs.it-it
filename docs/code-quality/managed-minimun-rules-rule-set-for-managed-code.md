---
title: "Set di regole minime gestite per codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
caps.handback.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Set di regole minime gestite per codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le regle Managed Minimum Rules sono orientate alla segnalazione dei problemi critici del codice, quali problemi di sicurezza, arresti anomali dell'applicazione e altri errori di logica e di progettazione rilevanti.  È necessario includere questo set di regole nei set di regole personalizzati creati per i progetti.  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi Disposable devono essere Disposable|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi Disposable devono essere eliminati|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|