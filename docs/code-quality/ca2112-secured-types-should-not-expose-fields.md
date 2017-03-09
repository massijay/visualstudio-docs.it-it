---
title: "CA2112: I tipi protetti non devono esporre campi | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
helpviewer_keywords: 
  - "CA2112"
  - "SecuredTypesShouldNotExposeFields"
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2112: I tipi protetti non devono esporre campi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Categoria|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto contiene campi pubblici ed è protetto da [Link Demands](../Topic/Link%20Demands.md).  
  
## Descrizione della regola  
 Se il codice ha accesso a un'istanza di un tipo protetta da una richiesta di collegamento, non è necessario che il codice soddisfi la richiesta di collegamento per accedere ai campi del tipo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare i campi come non pubblici e aggiungere metodi o proprietà pubbliche che restituiscano i dati dei campi.  I controlli di sicurezza LinkDemand sui tipi proteggono l'accesso alle proprietà e ai metodi del tipo.  Tuttavia, la sicurezza per l'accesso al codice non si applica ai campi.  
  
## Esclusione di avvisi  
 Per ragioni di sicurezza e di buona progettazione, è opportuno correggere le violazioni rendendo non pubblici i campi pubblici.  È possibile escludere un avviso da questa regola se il campo non contiene informazioni che devono rimanere protette e non ci si basa sul contenuto del campo.  
  
## Esempio  
 L'esempio riportato di seguito è composto da una libreria di tipi \(`SecuredTypeWithFields`\) con campi non protetti, da un tipo \(`Distributor`\) che crea istanze del tipo di libreria e istanze passate erroneamente a tipi privi dell'autorizzazione alla loro creazione e da codice di applicazione in grado di leggere i campi di un'istanza anche se non dispone dell'autorizzazione che protegge il tipo.  
  
 Il codice della libreria riportato di seguito viola la regola.  
  
 [!code-cs[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## Esempio  
 L'applicazione non può creare un'istanza a causa della richiesta di collegamento che protegge il tipo protetto.  La classe riportata di seguito consente all'applicazione di ottenere un'istanza del tipo sicuro.  
  
 [!code-cs[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## Esempio  
 L'applicazione riportata di seguito illustra come codice privo dell'autorizzazione ad accedere ai metodi di un tipo protetto possa accedere ai campi relativi.  
  
 [!code-cs[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Creazione di un'istanza di SecuredTypeWithFields.**  
**Secured type fields: 22, 33**  
**Changing secured type's field...**  
**Cached Object fields: 99, 33**   
## Regole correlate  
 [CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Vedere anche  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)