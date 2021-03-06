---
title: 'CA1900: I campi dei tipi di valore devono essere portabili | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f2d948d78f6b12352a3e4cfcb28aab41db3e873
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: I campi dei tipi di valore devono essere portabili
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Categoria|Microsoft.Portability|  
|Breaking Change|Sostanziale - Se il campo è visibile all'esterno dell'assembly.<br /><br /> Non sostanziale - Se il campo non è visibile all'esterno dell'assembly.|  
  
## <a name="cause"></a>Causa  
 Questa regola verifica che le strutture dichiarate con layout esplicito vengano allineate correttamente quando il marshalling a codice non gestito nei sistemi operativi a 64 bit. IA-64 non consente gli accessi alla memoria non allineata e il processo verrà arrestato in modo anomalo se questa violazione non viene risolto.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Strutture con layout esplicito che contiene campi non allineati causano arresti anomali nei sistemi operativi a 64 bit.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Devono disporre di tutti i campi che sono inferiori a 8 byte offset che siano un multiplo delle dimensioni e i campi che sono di 8 byte o superiori devono avere offset che sono un multiplo di 8. Un'altra soluzione consiste nell'utilizzare `LayoutKind.Sequential` anziché `LayoutKind.Explicit`, se ragionevole.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Questo avviso deve essere eliminato solo se si verifica l'errore.