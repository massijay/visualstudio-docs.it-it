---
title: "CA2201: Non generare tipi di eccezione riservati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseReservedExceptionTypes"
  - "CA2201"
helpviewer_keywords: 
  - "CA2201"
  - "DoNotRaiseReservedExceptionTypes"
ms.assetid: dd14ef5c-80e6-41a5-834e-eba8e2eae75e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2201: Non generare tipi di eccezione riservati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseReservedExceptionTypes|  
|CheckId|CA2201|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo ha generato un tipo di eccezione troppo generale o riservato dal runtime.  
  
## Descrizione della regola  
 I seguenti tipi di eccezione sono troppo generali per fornire informazioni sufficienti all'utente:  
  
-   <xref:System.Exception?displayProperty=fullName>  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.SystemException?displayProperty=fullName>  
  
 I seguenti tipi di eccezione sono riservati e devono essere generati esclusivamente da Common Language Runtime:  
  
-   <xref:System.ExecutionEngineException?displayProperty=fullName>  
  
-   <xref:System.IndexOutOfRangeException?displayProperty=fullName>  
  
-   <xref:System.NullReferenceException?displayProperty=fullName>  
  
-   <xref:System.OutOfMemoryException?displayProperty=fullName>  
  
 **Non generare eccezioni generali**  
  
 Se si genera un tipo di eccezione generale, ad esempio <xref:System.Exception> o <xref:System.SystemException> in una libreria o framework, i consumer saranno costretti a rilevare tutte le eccezioni, comprese quelle sconosciute che non sono progettati per gestire.  
  
 Generare invece un tipo più derivato che esista già nel framework, oppure creare un tipo personalizzato che derivi da <xref:System.Exception>.  
  
 **Generare eccezioni specifiche**  
  
 Nella tabella seguente vengono mostrati i parametri e le eccezioni da generare quando si convalida il parametro, incluso il parametro valore nella funzione di accesso impostata di una proprietà:  
  
|Descrizione parametro:|Eccezione|  
|----------------------------|---------------|  
|Riferimento `null`|<xref:System.ArgumentNullException?displayProperty=fullName>|  
|Al di fuori dell'intervallo di valori consentito \(ad esempio un indice per una raccolta o un'elenco\)|<xref:System.ArgumentOutOfRangeException?displayProperty=fullName>|  
|Valore `enum` non valido|<xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=fullName>|  
|Contiene un formato che non soddisfa le specifiche di parametro di un metodo \(ad esempio la stringa di formato per `ToString(String)`\)|<xref:System.FormatException?displayProperty=fullName>|  
|Altri parametri non validi|<xref:System.ArgumentException?displayProperty=fullName>|  
  
 Quando un'operazione è non valida per lo stato corrente di un oggetto viene generata <xref:System.InvalidOperationException?displayProperty=fullName>  
  
 Quando viene effettuata un'operazione su un oggetto che è stato eliminato, viene generata <xref:System.ObjectDisposedException?displayProperty=fullName>  
  
 Quando un'operazione non è supportata \(ad esempio in un oggetto **Stream.Write** sottoposto a override in un flusso aperto per la lettura\) viene generata <xref:System.NotSupportedException?displayProperty=fullName>  
  
 Quando una conversione comporterebbe un overflow \(ad esempio in caso di overload di un operatore di cast esplicito\) viene generata <xref:System.OverflowException?displayProperty=fullName>  
  
 Per tutte le altre situazioni, creare un tipo personalizzato che derivi da <xref:System.Exception> e generarlo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il tipo dell'eccezione generata in un tipo specifico non compreso tra quelli riservati.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)