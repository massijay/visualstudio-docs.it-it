---
title: "CA2229: Implementare costruttori di serializzazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2229: Implementare costruttori di serializzazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Il tipo implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, non è un delegato o un'interfaccia e una delle seguenti condizioni è vera:  
  
-   Il tipo non dispone di un costruttore che accetta un oggetto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> e un oggetto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(la firma del costruttore di serializzazione\).  
  
-   Il tipo è non sealed e il modificatore di accesso per il costruttore di serializzazione non è protetto \(a livello di famiglia\).  
  
-   Il tipo è sealed e il modificatore di accesso per il costruttore di serializzazione non è privato.  
  
## Descrizione della regola  
 Questa regola si applica ai tipi che supportano la serializzazione personalizzata.  Un tipo supporta la serializzazione personalizzata se implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable>.  Il costruttore di serializzazione è necessario per deserializzare o ricreare oggetti serializzati con il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare il costruttore di serializzazione.  Per una classe sealed, rendere il costruttore privato; in caso contrario renderlo protetto.  
  
## Esclusione di avvisi  
 Non escludere una violazione da questa regola.  Il tipo non risulterà deserializzabile e in molti scenari non funzionerà.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che soddisfa la regola.  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## Regole correlate  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Vedere anche  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>