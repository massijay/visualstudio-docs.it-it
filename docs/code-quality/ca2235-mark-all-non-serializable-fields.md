---
title: "CA2235: Contrassegnare tutti i campi non serializzabili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2235: Contrassegnare tutti i campi non serializzabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un campo di istanza di un tipo non serializzabile viene dichiarato in un tipo serializzabile.  
  
## Descrizione della regola  
 Un tipo serializzabile è contrassegnato con l'attributo <xref:System.SerializableAttribute?displayProperty=fullName>.  Quando il tipo è serializzato, viene generata un'eccezione <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> se un tipo contiene un campo di istanza di un tipo non serializzabile.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, applicare l'attributo <xref:System.NonSerializedAttribute?displayProperty=fullName> al campo non serializzabile.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola solo se viene dichiarato un tipo <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> che consente la serializzazione e la deserializzazione delle istanze del campo.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati due tipi: uno che viola la regola e uno che la soddisfa.  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## Regole correlate  
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)