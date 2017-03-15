---
title: "CA2120: Proteggere i costruttori di serializzazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2120"
  - "SecureSerializationConstructors"
helpviewer_keywords: 
  - "CA2120"
  - "SecureSerializationConstructors"
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2120: Proteggere i costruttori di serializzazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Il tipo implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, non è un delegato né un'interfaccia ed è dichiarato in un assembly che consente i chiamanti parzialmente attendibili.  Il tipo dispone di un costruttore che accetta un oggetto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> e un oggetto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> \(la firma del costruttore di serializzazione\).  Questo costruttore non è protetto da un controllo di sicurezza, ma uno o più costruttori regolari nel tipo sono protetti.  
  
## Descrizione della regola  
 Questa regola si applica ai tipi che supportano la serializzazione personalizzata.  Un tipo supporta la serializzazione personalizzata se implementa l'interfaccia <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>.  Il costruttore di serializzazione è richiesto e viene utilizzato per deserializzare o ricreare oggetti serializzati mediante il metodo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.  Poiché il costruttore di serializzazione alloca e inizializza oggetti, i controlli di sicurezza presenti sui costruttori regolari devono anche essere presenti sul costruttore di serializzazione.  Se si viola questa regola, i chiamanti che non possono creare in altro modo un'istanza possono utilizzare a tal fine il costruttore di serializzazione.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, proteggere il costruttore di serializzazione con richieste di sicurezza identiche a quelle che proteggono gli altri costruttori.  
  
## Esclusione di avvisi  
 Non escludere una violazione da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola la regola.  
  
 [!code-cs[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## Regole correlate  
 [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: Contrassegnare i tipi ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Vedere anche  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>