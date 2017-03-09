---
title: "CA2107: Controllare l&#39;utilizzo di Deny e PermitOnly | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2107"
  - "ReviewDenyAndPermitOnlyUsage"
helpviewer_keywords: 
  - "ReviewDenyAndPermitOnlyUsage"
  - "CA2107"
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2107: Controllare l&#39;utilizzo di Deny e PermitOnly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|Categoria|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo contiene un controllo di sicurezza che specifica l'azione di sicurezza PermitOnly o Deny.  
  
## Descrizione della regola  
 Le azioni di sicurezza [Using the PermitOnly Method](http://msdn.microsoft.com/it-it/8c7bdb7f-882f-45b7-908c-6cbaa1767649) e <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName> devono essere utilizzate esclusivamente da utenti che possiedono una conoscenza approfondita della sicurezza [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Il codice che utilizza queste azioni di sicurezza deve essere sottoposto a una revisione della sicurezza.  
  
 Deny altera il comportamento predefinito del percorso chiamate nello stack che si verifica in risposta a una richiesta di sicurezza.  Consente di specificare le autorizzazioni che non devono essere concesse per la durata del metodo Deny, indipendentemente dalle autorizzazioni effettive dei chiamanti nello stack di chiamate.  Se nel percorso stack viene rilevato un metodo protetto da Deny e l'autorizzazione richiesta è inclusa nelle autorizzazioni negate, il percorso stack avrà esito negativo.  Anche PermitOnly altera il comportamento predefinito del percorso chiamate nello stack.  Consente al codice di specificare solo le autorizzazioni che è possibile concedere, indipendentemente dalle autorizzazioni dei chiamanti.  Se nel percorso stack viene rilevato un metodo protetto da PermitOnly e le autorizzazioni richieste non sono incluse nelle autorizzazioni specificate da PermitOnly, il percorso stack avrà esito negativo.  
  
 Il codice che si basa su queste azioni deve essere valutato attentamente per individuarne le vulnerabilità di sicurezza a causa della limitata utilità e del particolare comportamento.  Si consideri quanto segue.  
  
-   Deny e PermitOnly non hanno effetto su [Link Demands](../Topic/Link%20Demands.md).  
  
-   Se Deny o PermitOnly si verifica nello stesso stack frame della richiesta che causa il percorso stack, le azioni di sicurezza non avranno effetto.  
  
-   I valori utilizzati per costruire le autorizzazioni basate su percorso possono in genere essere specificati in molti modi.  Negando l'accesso a un formato del percorso non si nega l'accesso a tutte le forme.  Se ad esempio una condivisione file \\\\Server\\Condivisione è mappata su un'unità di rete X:, per negare l'accesso a un file in tale condivisione sarà necessario negare \\\\Server\\Condivisione\\File, X:\\File e ogni altro percorso che consente di accedere al file.  
  
-   Un metodo <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> può terminare un percorso stack prima che venga raggiunta l'operazione Deny o PermitOnly.  
  
-   Se l'operazione Deny produce un qualsiasi effetto, ovvero se un'autorizzazione di un chiamante è bloccata da Deny, il chiamante potrà accedere direttamente alla risorsa protetta, ignorando Deny.  Analogamente, se il chiamante non dispone dell'autorizzazione negata, il percorso stack avrà esito negativo senza l'operazione Deny.  
  
## Come correggere le violazioni  
 Qualsiasi utilizzo di queste azioni di sicurezza causerà una violazione.  Per correggere una violazione, non utilizzare queste azioni di sicurezza.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola dopo aver completato una revisione della sicurezza.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate alcune limitazioni di Deny.  
  
 La libreria riportata di seguito contiene una classe con due metodi identici, ad eccezione delle richieste di sicurezza che li proteggono.  
  
 [!CODE [FxCop.Security.PermitAndDeny#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny#1)]  
  
## Esempio  
 L'applicazione riportata di seguito dimostra gli effetti di Deny sui metodi protetti della libreria.  
  
 [!code-cs[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Demand: Caller's Deny has no effect on Demand with the asserted permission.**  
**LinkDemand: Caller's Deny has no effect on LinkDemand with the asserted permission.**  
**LinkDemand: Caller's Deny has no effect with LinkDemand\-protected code.**  
**LinkDemand: This Deny has no effect with LinkDemand\-protected code.**   
## Vedere anche  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Overriding Security Checks](http://msdn.microsoft.com/it-it/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Using the PermitOnly Method](http://msdn.microsoft.com/it-it/8c7bdb7f-882f-45b7-908c-6cbaa1767649)