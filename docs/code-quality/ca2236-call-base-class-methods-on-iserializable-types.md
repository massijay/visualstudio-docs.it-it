---
title: "CA2236: Chiamare metodi della classe base su tipi ISerializable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2236: Chiamare metodi della classe base su tipi ISerializable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo deriva da un tipo che implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> e si verifica una delle condizioni riportate di seguito:  
  
-   Il tipo implementa il costruttore di serializzazione, ovvero un costruttore con la firma del parametro <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, ma non chiama il costruttore di serializzazione del tipo di base.  
  
-   Il tipo implementa il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ma non chiama il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> del tipo di base.  
  
## Descrizione della regola  
 In un processo di serializzazione personalizzato, un tipo implementa il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> per serializzare i campi relativi e il costruttore di serializzazione per deserializzare i campi.  Se il tipo deriva da un tipo che implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable>, il costruttore di serializzazione e il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> del tipo di base devono essere chiamati per serializzare o deserializzare i campi del tipo di base.  In caso contrario, il tipo non verrà serializzato e deserializzato correttamente.  Si noti che se il tipo derivato non aggiunge alcun nuovo campo, il tipo non deve implementare il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> né il costruttore di serializzazione oppure chiamare gli equivalenti del tipo di base.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare il costruttore di serializzazione o il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> del tipo di base dal costruttore o dal metodo del tipo derivato corrispondente.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo derivato che soddisfa la regola chiamando il costruttore di serializzazione e il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> della classe base.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## Regole correlate  
 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Fornire metodi di deserializzazione per i campi facoltativi](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)