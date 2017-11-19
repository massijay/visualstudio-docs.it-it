---
title: "CA1501: Evitare ereditarietà eccessiva | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3c09a3367985613072944c5f74f0c708a149da15
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evitare ereditarietà eccessiva
|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Categoria|Microsoft.Maintainability|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo si trova oltre il quarto livello di annidamento nella gerarchia di ereditarietà.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Le gerarchie di tipi eccessivamente annidate possono comportare difficoltà di comprensione e gestione. Questa regola consente di limitare analisi alle gerarchie nello stesso modulo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, derivare il tipo da un tipo di base meno annidato nella gerarchia di ereditarietà o eliminare alcuni dei tipi di base intermedi.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola. Tuttavia, il codice potrebbe essere più difficile da gestire. Si noti che, a seconda della visibilità dei tipi di base, la risoluzione delle violazioni di questa regola potrebbe creare modifiche di rilievo. Ad esempio, la rimozione di tipi di base pubblici è una modifica di rilievo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola.  
  
 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]