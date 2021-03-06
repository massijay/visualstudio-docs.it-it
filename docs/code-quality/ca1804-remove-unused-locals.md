---
title: 'CA1804: Rimuovere locali non utilizzati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9217f3109c6ef03de33e444e723caa585d065efb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: rimuovere locali non utilizzati
|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Categoria|Microsoft. Performance|  
|Breaking Change|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un metodo dichiara una variabile locale, ma non utilizzare la variabile tranne probabilmente come destinatario di un'istruzione di assegnazione. Per l'analisi da questa regola, l'assembly testato deve essere compilato con informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Le variabili locali inutilizzate e le assegnazioni non necessarie comportano un aumento delle dimensioni dell'assembly e una riduzione delle prestazioni.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o utilizzare la variabile locale. Si noti che il compilatore c# che è incluso in [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] rimuove le variabili locali inutilizzate quando il `optimize` opzione è abilitata.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola se la variabile è stata creata dal compilatore. È inoltre sicura per escludere un avviso da questa regola o disabilitare la regola, se le prestazioni e manutenzione del codice non sono aspetti più importanti.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra alcune variabili locali inutilizzate.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1809: Evitare un numero eccessivo di variabili locali](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Evitare il codice privato non chiamato](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Rivedere i parametri non usati](../code-quality/ca1801-review-unused-parameters.md)