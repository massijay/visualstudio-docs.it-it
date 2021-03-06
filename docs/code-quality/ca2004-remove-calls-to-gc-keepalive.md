---
title: 'CA2004: Rimuovere le chiamate a GC. KeepAlive | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: edb47391872da6754e39a27d2e8a50dc61293af1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Rimuovere le chiamate a GC.KeepAlive
|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Categoria|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Utilizzo di classi `SafeHandle` ma contengono ancora chiamate a `GC.KeepAlive`.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Se si desidera convertire in `SafeHandle` utilizzo, rimuovere tutte le chiamate a `GC.KeepAlive` (oggetto). In questo caso, le classi non necessario chiamare `GC.KeepAlive`, supponendo che non dispone di un finalizzatore, ma si basano su `SafeHandle` per completare l'handle del sistema operativo per loro.  Anche se il costo di lasciare in una chiamata a `GC.KeepAlive` potrebbe essere trascurabile in termini di prestazioni, la percezione che una chiamata a `GC.KeepAlive` sia necessaria o sufficiente per risolvere un problema che potrebbe non esistere più difficile il codice di durata Gestisci.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rimuovere le chiamate a `GC.KeepAlive`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare questo avviso solo se non è tecnicamente corretto convertire in `SafeHandle` utilizzo della classe.