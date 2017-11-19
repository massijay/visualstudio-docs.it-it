---
title: 'CA1724: I nomi dei tipi non devono corrispondere gli spazi dei nomi | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 556fd9eee1bc453d4f9782459050367e18a3193b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724: I nomi dei tipi non devono corrispondere agli spazi dei nomi
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Categoria|Microsoft. naming|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un nome di tipo corrisponde a un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] spazi dei nomi in un confronto tra maiuscole e minuscole.  
  
## <a name="rule-description"></a>Descrizione della regola  
 I nomi dei tipi non devono corrispondere ai nomi degli spazi dei nomi definiti nella libreria di classi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. La violazione di questa regola può ridurre l'utilizzabilità della libreria.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Selezionare un nome di tipo che corrisponde al nome di un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] spazio dei nomi della libreria di classe.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Per un nuovo sviluppo, non noto possono verificarsi scenari in cui è necessario escludere un avviso da questa regola. Prima di eliminare l'avviso, valutare attentamente come potrebbero confondere gli utenti della raccolta dal nome corrispondente. Per le librerie fornite, potrebbe essere necessario escludere un avviso da questa regola.