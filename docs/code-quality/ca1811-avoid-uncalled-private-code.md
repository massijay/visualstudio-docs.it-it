---
title: "CA1811: Evitare il codice privato non chiamato | Microsoft Docs"
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
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1811: Evitare il codice privato non chiamato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Category|Microsoft.Performance|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro privato o interno \(a livello di assembly\) non presenta chiamanti nell'assembly, non viene richiamato da Common Language Runtime e non viene richiamato da un delegato.  I seguenti membri non sono controllati da questa regola:  
  
-   Membri di interfaccia espliciti.  
  
-   Costruttori statici.  
  
-   Costruttori di serializzazione.  
  
-   Metodi contrassegnati con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Membri costituiti da override.  
  
## Descrizione della regola  
 La regola può segnalare falsi positivi se si verificano punti di ingresso non attualmente identificati dalla logica della regola.  È inoltre possibile che un compilatore crei del codice non chiamabile in un assembly.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il codice non chiamabile o aggiungere del codice che lo chiami.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura.  
  
## Regole correlate  
 [CA1812: Evitare classi interne prive di istanze](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Rivedere i parametri inutilizzati](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: rimuovere locali non utilizzati](../code-quality/ca1804-remove-unused-locals.md)