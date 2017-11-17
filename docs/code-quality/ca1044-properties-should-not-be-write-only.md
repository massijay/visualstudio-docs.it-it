---
title: "CA1044: Proprietà non devono essere in sola scrittura | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c81c76fc20262d781e89e8ec786f7a640f6ee026
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Le proprietà non devono essere in sola scrittura
|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Categoria|Microsoft. Design|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 La proprietà pubblica o protetta è una funzione di accesso set, ma non dispone di una funzione di accesso get.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Ottenere le funzioni di accesso forniscono l'accesso in lettura a una proprietà e funzioni di accesso set forniscono l'accesso in scrittura. Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura. Questo avviene perché consentire a un utente di impostare un valore e quindi impedire all'utente di visualizzare il valore non fornisce alcuna protezione. Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere una funzione di accesso get della proprietà. In alternativa, se il comportamento di una proprietà di sola scrittura è necessario, eseguire la conversione di questa proprietà a un metodo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È consigliabile che non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, `BadClassWithWriteOnlyProperty` è un tipo con una proprietà di sola scrittura. `GoodClassWithReadWriteProperty`contiene il codice corretto.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]