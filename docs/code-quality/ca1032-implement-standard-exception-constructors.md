---
title: "CA1032: Implementare costruttori di eccezioni standard | Microsoft Docs"
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
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1032: Implementare costruttori di eccezioni standard
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo estende <xref:System.Exception?displayProperty=fullName> e non dichiara tutti i costruttori necessari.  
  
## Descrizione della regola  
 I tipi di eccezione devono implementare i seguenti costruttori:  
  
-   public NewException\(\)  
  
-   public NewException\(string\)  
  
-   public NewException\(string, Exception\)  
  
-   protected o private NewException\(SerializationInfo, StreamingContext\)  
  
 Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni.  Il costruttore con la firma `NewException(string, Exception)`, ad esempio, viene utilizzato per creare eccezioni causate da altre eccezioni.  Senza questo costruttore, non è possibile creare e generare un'istanza dell'eccezione personalizzata che contiene un'eccezione interna \(annidata\), operazione prevista per il codice gestito in tale situazione.  I primi tre costruttori di eccezioni sono pubblici per convenzione.  Il quarto costruttore è protetto nelle classi non sealed e privato nelle classi sealed.  Per ulteriori informazioni, vedere [CA2229: Implementare costruttori di serializzazione](../code-quality/ca2229-implement-serialization-constructors.md).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere i costruttori mancanti all'eccezione e assicurarsi che dispongano dell'accessibilità corretta.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura quando la violazione è causata dall'utilizzo di un livello di accesso diverso per i costruttori pubblici.  
  
## Esempio  
 L'esempio riportato di seguito contiene un tipo di eccezione che viola questa regola e un tipo di eccezione implementato correttamente.  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]