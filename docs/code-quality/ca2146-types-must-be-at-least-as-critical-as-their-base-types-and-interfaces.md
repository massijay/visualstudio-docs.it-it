---
title: "CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2146: I tipi devono essere Critical almeno come le interfacce e i tipi base relativi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Il tipo Trasparent derivato da un tipo contrassegnato da <xref:System.Security.SecuritySafeCriticalAttribute> o da <xref:System.Security.SecurityCriticalAttribute> oppure un tipo che è contrassegnato dall'attributo <xref:System.Security.SecuritySafeCriticalAttribute> è derivato da un tipo contrassegnato con l'attributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descrizione della regola  
 Questa regola viene attivata quando un tipo derivato dispone di un attributo di trasparenza di sicurezza che non è critico come il tipo di base o l'interfaccia implementata.  Solo i tipi critici possono derivare da tipi di base critici o implementare interfacce critiche e solo tipi critici o critici per la sicurezza possono derivare da tipi di base critici per la sicurezza o implementare interfacce critiche per la sicurezza.  Violazioni di questa regola della trasparenza di livello 2 risultino in un <xref:System.TypeLoadException> per il tipo derivato.  
  
## Come correggere le violazioni  
 Per correggere questa violazione, contrassegnare il tipo derivato o di implementazione con un attributo di trasparenza che è almeno critico quanto il tipo di base o l'interfaccia.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]