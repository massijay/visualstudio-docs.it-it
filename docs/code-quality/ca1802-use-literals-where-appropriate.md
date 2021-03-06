---
title: 'CA1802: Utilizza valori letterali dove appropriato | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 66ee20e099de0206664390623b7a50c5fec723a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Utilizza valori letterali dove appropriato
|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Categoria|Microsoft. Performance|  
|Breaking Change|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un campo viene dichiarato `static` e `readonly` (`Shared` e `ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) e viene inizializzato con un valore calcolabile in fase di compilazione.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Il valore di un `static``readonly` campo viene calcolato in fase di esecuzione quando viene chiamato il costruttore statico per il tipo dichiarante. Se il `static``readonly` campo viene inizializzato quando viene dichiarata e un costruttore statico non è dichiarato in modo esplicito, il compilatore genera un costruttore per inizializzare il campo statico.  
  
 Il valore di un `const` campo viene calcolato in fase di compilazione e archiviato nei metadati, aumentando le prestazioni di runtime quando viene confrontata con un `static``readonly` campo.  
  
 Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un `const` in modo che il valore viene calcolato in fase di compilazione anziché in fase di esecuzione.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il `static` e `readonly` modificatori con il `const` modificatore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile escludere un avviso da questa regola o disabilitare la regola, se le prestazioni non è un problema.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo, `UseReadOnly`, che viola la regola e un tipo, `UseConstant`, che soddisfa la regola.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]