---
title: Set di regole minime gestite per codice gestito | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac5ec4db1fe36d7e92c4f9062f8d0c28bae2263e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Gestito minimo set di regole per il codice gestito
Le regole minime gestite concentrarsi sui problemi più critici del codice, inclusi i potenziali problemi di sicurezza, arresti anomali delle applicazioni e altri errori di logica e di progettazione rilevanti. È necessario includere questo set di regole nel set di regole personalizzati creati per i progetti.  
  
|Regola|Descrizione|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi disposable devono essere disposable|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi Disposable devono essere eliminati.|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Overload dell'operatore è uguale all'override di ValueType. Equals|
