---
title: "CA2222: Non diminuire la visibilità di membri ereditati | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 520882b8d1b24cc7bc346ae185de8f186e4fa163
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Non diminuire la visibilità di membri ereditati
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Categoria|Microsoft. Usage|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
 Un metodo privato in un tipo non sealed ha una firma identica a un metodo pubblico dichiarato in un tipo di base. Il metodo privato non è finale.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Non modificare il modificatore di accesso per i membri ereditati. La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo. Se il membro viene reso privato e il tipo è non bloccato, l'ereditarietà di tipi può chiamare l'implementazione di pubblico ultimo del metodo nella gerarchia di ereditarietà. Se è necessario modificare il modificatore di accesso, il metodo deve essere contrassegnato come finale o il relativo tipo deve essere sealed per impedire l'override del metodo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare l'accesso per essere pubblici. In alternativa, se supporta il linguaggio di programmazione, è possibile rendere il metodo finale.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola questa regola.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]