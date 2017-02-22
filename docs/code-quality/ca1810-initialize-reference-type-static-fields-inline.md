---
title: "CA1810: Inizializzare i campi statici del tipo di riferimento inline | Microsoft Docs"
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
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1810: Inizializzare i campi statici del tipo di riferimento inline
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo di riferimento dichiara un costruttore statico esplicito.  
  
## Descrizione della regola  
 Quando un tipo dichiara un costruttore statico esplicito, tramite il compilatore JIT \(Just\-In\-Time\) viene aggiunto un controllo a ogni metodo statico del tipo e a ogni costruttore di istanza del tipo per assicurare che il costruttore statico sia stato precedentemente chiamato.  L'inizializzazione statica viene attivata quando si accede a un membro statico o quando viene creata un'istanza del tipo.  L'inizializzazione statica tuttavia non viene attivata se si dichiara una variabile del tipo ma non la si utilizza, una condizione importante se l'inizializzazione modifica lo stato globale.  
  
 Quando tutti i dati statici vengono inizializzati inline e non viene dichiarato un costruttore statico esplicito, i compilatori MSIL \(Microsoft Intermediate Language\) aggiungono alla definizione di tipo MSIL il flag `beforefieldinit` e un costruttore statico implicito che inizializza i dati statici.  Quando il compilatore JIT rileva il flag `beforefieldinit`, nella maggior parte dei casi i controlli del costruttore statico non vengono aggiunti.  L'inizializzazione statica viene sicuramente eseguita prima che si acceda a qualsiasi campo statico, ma non prima che venga richiamato un metodo statico o un costruttore di istanza.  Notare che l'inizializzazione statica può essere eseguita in qualsiasi momento dopo la dichiarazione di una variabile del tipo.  
  
 I controlli dei costruttori statici possono ridurre le prestazioni.  Un costruttore statico viene spesso utilizzato solo per inizializzare campi statici, nel qual caso è sufficiente assicurare che l'inizializzazione statica venga eseguita prima del primo accesso a un campo statico.  Il comportamento di `beforefieldinit` è appropriato per questi tipi e per la maggior parte degli altri,  ma non lo è solo quando l'inizializzazione statica influisce sullo stato globale e viene soddisfatta una delle seguenti condizioni:  
  
-   L'effetto sullo stato globale è dispendioso e non è necessario se il tipo non è utilizzato.  
  
-   È possibile accedere agli effetti sullo stato globale senza accedere ad alcun campo statico del tipo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se le prestazioni non sono importanti o se le modifiche allo stato globale causate dall'inizializzazione statica sono dispendiose o devono necessariamente essere eseguite prima che venga chiamato un metodo statico del tipo o venga creata un'istanza del tipo.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati il tipo `StaticConstructor`, che viola la regola, e il tipo `NoStaticConstructor`, che sostituisce il costruttore statico con l'inizializzazione inline per soddisfare la regola.  
  
 [!code-cs[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Si noti l'aggiunta del flag `beforefieldinit` alla definizione MSIL della classe `NoStaticConstructor`.  
  
  **Il .class StaticConstructor auto ANSI pubblico estende \[mscorlib\]System.Object { } \/\/ fine della classe StaticConstructor .class auto ANSI pubblica di beforefieldinit NoStaticConstructor che estende \[mscorlib\]System.Object { } \/\/ la fine della classe NoStaticConstructor**   
## Regole correlate  
 [CA2207: Inizializzare i campi statici dei tipi di valore inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)