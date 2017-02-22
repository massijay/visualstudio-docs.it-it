---
title: "CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo visibile esternamente implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e non è contrassegnato con l'attributo <xref:System.SerializableAttribute?displayProperty=fullName>.  La regola ignora i tipi derivati il cui tipo di base non è serializzabile.  
  
## Descrizione della regola  
 Affinché i tipi vengano riconosciuti come serializzabili in Common Language Runtime, è necessario che siano contrassegnati con l'attributo <xref:System.SerializableAttribute> anche se il tipo utilizza una routine di serializzazione personalizzata tramite l'implementazione dell'interfaccia <xref:System.Runtime.Serialization.ISerializable>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, applicare l'attributo <xref:System.SerializableAttribute> al tipo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola per le classi di eccezioni perché per funzionare correttamente in diversi domini applicazione è necessario che siano serializzabili.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  Rimuovere il commento dalla riga dell'attributo <xref:System.SerializableAttribute> per soddisfare la regola.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## Regole correlate  
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)