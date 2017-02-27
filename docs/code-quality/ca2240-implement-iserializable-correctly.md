---
title: "CA2240: Implementare ISerializable in modo corretto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2240"
  - "ImplementISerializableCorrectly"
helpviewer_keywords: 
  - "CA2240"
  - "ImplementISerializableCorrectly"
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA2240: Implementare ISerializable in modo corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo visibile esternamente può essere assegnato all'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e viene soddisfatta una delle seguenti condizioni:  
  
-   Il tipo eredita ma non esegue l'override del metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> e il tipo dichiara campi di istanza non contrassegnati con l'attributo <xref:System.NonSerializedAttribute?displayProperty=fullName>.  
  
-   Il tipo non è sealed e implementa un metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> che non è visibile esternamente e sottoponibile a override.  
  
## Descrizione della regola  
 I campi di istanza dichiarati in un tipo che eredita l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> non sono inclusi automaticamente nel processo di serializzazione.  Per includere i campi, il tipo deve implementare il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> e il costruttore di serializzazione.  Se i campi non devono essere serializzati, applicare a essi l'attributo <xref:System.NonSerializedAttribute> per indicare esplicitamente la decisione.  
  
 In tipi non sealed, le implementazioni del metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> devono essere visibili esternamente.  Pertanto, il metodo può essere chiamato dai tipi derivati ed è sottoponibile a override.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere visibile e sottoponibile a override il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> e accertarsi che tutti i campi di istanza siano inclusi nel processo di serializzazione o contrassegnati esplicitamente con l'attributo <xref:System.NonSerializedAttribute>.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati due tipi serializzabili che violano la regola.  
  
 [!code-cs[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## Esempio  
 Nell'esempio seguente vengono risolte le due violazioni precedenti tramite un'implementazione sottoponibile a override di [ISerializable.GetObjectData](assetId:///ISerializable.GetObjectData?qualifyHint=False&autoUpgrade=False) nella classe Book e un'implementazione di assetId:///ISerializable.GetObjectData?qualifyHint=False&autoUpgrade=False nella classe Library.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## Regole correlate  
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)