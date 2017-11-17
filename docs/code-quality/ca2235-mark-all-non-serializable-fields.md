---
title: 'CA2235: Contrassegnare tutti i campi non serializzabili | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6489cf400dd2f67c08ff4dba3bf6a1eda4ec46e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Contrassegnare tutti i campi non serializzabili
|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Categoria|Microsoft. Usage|  
|Breaking Change|Non importante|  
  
## <a name="cause"></a>Causa  
 Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un tipo serializzabile è contrassegnato con il <xref:System.SerializableAttribute?displayProperty=fullName> attributo. Quando viene serializzato il tipo, un <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> eccezione viene generata se un tipo contiene un campo di istanza di un tipo che non è serializzabile.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, applicare il <xref:System.NonSerializedAttribute?displayProperty=fullName> attributo per il campo che non è serializzabile.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola solo se un <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo viene dichiarato che consente di istanze del campo da serializzare e deserializzare.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che soddisfa la regola.  
  
 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Specificare metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)