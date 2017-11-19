---
title: 'CA2131: I tipi SecurityCritical possono non partecipare all''equivalenza del tipo | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 90789a7a632084d157f94f72deb1c06370223056
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: I tipi SecurityCritical possono non partecipare all'equivalenza del tipo
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Categoria|Microsoft.Security|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo partecipa all'equivalenza del tipo e il tipo stesso o un membro o un campo del tipo, è contrassegnato con il <xref:System.Security.SecurityCriticalAttribute> attributo.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola viene attivata su qualsiasi tipo critico o a tipi che contengono metodi o campi critici che partecipano all'equivalenza del tipo. Quando CLR rileva tale tipo, non è possibile caricarlo con un <xref:System.TypeLoadException> in fase di esecuzione. In genere, questa regola funziona solo quando gli utenti implementano l'equivalenza del tipo manualmente piuttosto che basarsi su tlbimp e i compilatori per fare l'equivalenza del tipo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere l'attributo SecurityCritical.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Gli esempi seguenti illustrano un'interfaccia, un metodo e un campo che causa l'attivazione di questa regola.  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 [Codice SecurityTransparent, livello 2](http://msdn.microsoft.com/Library/4d05610a-0da6-4f08-acea-d54c9d6143c0)