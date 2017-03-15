---
title: "CA2207: Inizializzare i campi statici dei tipi di valore inline | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2207: Inizializzare i campi statici dei tipi di valore inline
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo di valore dichiara un costruttore statico esplicito.  
  
## Descrizione della regola  
 Quando viene dichiarato, un tipo di valore viene sottoposto a un'inizializzazione predefinita in cui tutti i campi di tipo di valore vengono impostati su zero e tutti i campi di tipo di riferimento vengono impostati su `null` \(`Nothing` in Visual Basic\).  L'esecuzione di un costruttore statico esplicito è garantita solo prima che venga chiamato un costruttore di istanza o un membro statico del tipo.  Se pertanto il tipo viene creato senza chiamare un costruttore di istanza, il costruttore statico non viene necessariamente eseguito.  
  
 Se tutti i dati statici vengono inizializzati inline e non viene dichiarato alcun costruttore statico esplicito, i compilatori C\# e Visual Basic aggiungono il flag `beforefieldinit` alla definizione di classe MSIL.  I compilatori aggiungono anche un costruttore statico privato contenente il codice di inizializzazione statico.  L'esecuzione di questo costruttore statico privato è garantita prima che venga effettuato l'accesso a qualsiasi campo statico del tipo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, inizializzare tutti i dati statici quando vengono dichiarati e rimuovere il costruttore statico.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA1810: Inizializzare i campi statici del tipo di riferimento inline](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)