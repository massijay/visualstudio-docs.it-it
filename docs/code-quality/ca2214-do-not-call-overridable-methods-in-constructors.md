---
title: 'CA2214: Non chiamare metodi sottoponibili a override nei costruttori | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bbe640ac82c159b39721ddac27b9d65926c60647
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Non chiamare metodi sottoponibili a override nei costruttori
|||  
|-|-|  
|TypeName|DoNotCallOverridableMethodsInConstructors|  
|CheckId|CA2214|  
|Categoria|Microsoft. Usage|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
 Il costruttore di un tipo non sealed chiama un metodo virtuale definito nella relativa classe.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Quando viene chiamato un metodo virtuale, il tipo effettivo che esegue il metodo non è selezionato in fase di esecuzione. Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non è stata eseguita.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, non chiamare metodi virtuali da un tipo all'interno di costruttori del tipo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola. Il costruttore deve essere riprogettato per eliminare la chiamata al metodo virtuale.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'effetto della violazione di questa regola. L'applicazione di test crea un'istanza di `DerivedType`, che comporta la relativa classe base (`BadlyConstructedType`) esecuzione del costruttore. `BadlyConstructedType`del costruttore chiama in modo non corretto del metodo virtuale `DoSomething`. Come illustrato nell'output, `DerivedType.DoSomething()` viene eseguito prima del `DerivedType`dell'esecuzione del costruttore.  
  
 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]  
  
 Questo esempio produce il seguente output:  
  
 **Chiamare il costruttore base.**  
**Viene chiamato DoSomething derivata - inizializzato? No**  
**Chiamare il metodo derivato ctor.**