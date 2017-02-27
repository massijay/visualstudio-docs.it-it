---
title: "CA2136: I membri non devono avere annotazioni di trasparenza in conflitto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2127"
  - "SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode"
  - "CA2136"
helpviewer_keywords: 
  - "CA2127"
  - "SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode"
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2136: I membri non devono avere annotazioni di trasparenza in conflitto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Questa regola funziona quando un membro del tipo è contrassegnato da un attributo di sicurezza <xref:System.Security> che dispone di una trasparenza diversa dall'attributo di sicurezza di un contenitore del membro.  
  
## Descrizione della regola  
 Gli attributi di trasparenza vengono applicati da elementi di codice con un ambito più ampio a elementi con ambito più ridotto.  Gli attributi di trasparenza di elementi di codice che presentano un ambito più ampio hanno la precedenza su quelli contenuti nel primo elemento.  Ad esempio, una classe contrassegnata con l'attributo <xref:System.Security.SecurityCriticalAttribute> non può contenere un metodo contrassegnato con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Come correggere le violazioni  
 Per correggere questa violazione, rimuovere l'attributo di sicurezza dall'elemento di codice che ha uno scopo minore o modificarne l'attributo in modo che sia uguale all'elemento di codice che lo contiene.  
  
## Esclusione di avvisi  
 Non escludere gli avvisi da questa regola.  
  
## Esempio  
 Nel seguente esempio, un metodo è contrassegnato con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute> ed è un membro di una classe contrassegnata con l'attributo <xref:System.Security.SecurityCriticalAttribute>.  L'attributo SafeSecure deve essere rimosso.  
  
 [!code-cs[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]