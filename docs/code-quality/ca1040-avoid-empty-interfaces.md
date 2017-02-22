---
title: "CA1040: Evitare l&#39;utilizzo di interfacce vuote | Microsoft Docs"
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
  - "CA1040"
  - "AvoidEmptyInterfaces"
helpviewer_keywords: 
  - "AvoidEmptyInterfaces"
  - "CA1040"
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1040: Evitare l&#39;utilizzo di interfacce vuote
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|CheckId|CA1040|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 L'interfaccia non dichiara alcun membro né implementa due o più interfacce.  
  
## Descrizione della regola  
 Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo.  La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà.  Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia.  Un'interfaccia vuota non definisce alcun membro.  Di conseguenza, non definisce un contratto che può essere implementato.  
  
 Se la progettazione include interfacce vuote di cui si prevede l'implementazione da parte di tipi, è probabile che sia in uso un'interfaccia come marcatore o come mezzo per identificare un gruppo di tipi.  Se questa identificazione si verifica in fase di esecuzione, la procedura corretta consiste nell'utilizzare un attributo personalizzato.  Utilizzare la presenza o l'assenza dell'attributo oppure le proprietà dello stesso per identificare i tipi di destinazione.  Se l'identificazione deve verificarsi in fase di compilazione, l'utilizzo di un'interfaccia vuota è accettabile.  
  
## Come correggere le violazioni  
 Rimuovere l'interfaccia o aggiungervi membri.  Se l'interfaccia vuota viene utilizzata per etichettare un insieme di tipi, sostituirla con un attributo personalizzato.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura quando l'interfaccia viene utilizzata per identificare un set di tipi in fase di compilazione.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata un'interfaccia vuota.  
  
 [!code-cs[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]