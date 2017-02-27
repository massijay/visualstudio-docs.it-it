---
title: "CA2239: Fornire metodi di deserializzazione per i campi facoltativi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2239: Fornire metodi di deserializzazione per i campi facoltativi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo presenta un campo contrassegnato con l'attributo <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> e il tipo non fornisce metodi di gestione degli eventi di deserializzazione.  
  
## Descrizione della regola  
 L'attributo <xref:System.Runtime.Serialization.OptionalFieldAttribute> non influisce sulla deserializzazione; un campo contrassegnato con l'attributo è serializzato.  Il campo viene, tuttavia, ignorato durante la deserializzazione e mantiene il valore predefinito associato al tipo relativo.  Per impostare il campo durante il processo di deserializzazione, è necessario dichiarare i gestori degli eventi di deserializzazione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere al tipo i metodi di gestione degli eventi di deserializzazione.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il campo deve essere ignorato durante il processo di deserializzazione.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo con un campo opzionale e metodi di gestione degli eventi di deserializzazione.  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## Regole correlate  
 [CA2236: Chiamare metodi della classe base su tipi ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementare ISerializable in modo corretto](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Implementare correttamente i metodi di serializzazione](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Contrassegnare tutti i campi non serializzabili](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: Proteggere i costruttori di serializzazione](../code-quality/ca2120-secure-serialization-constructors.md)