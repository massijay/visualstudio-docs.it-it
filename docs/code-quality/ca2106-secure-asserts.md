---
title: "CA2106: Asserzioni protette | Microsoft Docs"
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
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106: Asserzioni protette
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo asserisce un'autorizzazione e non vengono eseguiti controlli di sicurezza sul chiamante.  
  
## Descrizione della regola  
 Quando si asserisce un'autorizzazione di sicurezza senza eseguire alcun controllo di sicurezza, nel codice potrebbero restare punti deboli nella sicurezza.  Un percorso stack di sicurezza si arresta quando un'autorizzazione di sicurezza è asserita.  Se si asserisce un'autorizzazione senza eseguire alcun controllo sul chiamante, il chiamante potrebbe eseguire indirettamente il codice utilizzando le autorizzazioni.  Le asserzioni senza controlli di sicurezza sono consentite solo quando si è certi che l'asserzione non può essere utilizzata in modo dannoso.  Un'asserzione è innocua se il codice chiamato è innocuo o gli utenti non possono passare informazioni arbitrarie al codice chiamato.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere una richiesta di sicurezza al metodo o al tipo che lo dichiara.  
  
## Esclusione di avvisi  
 Escludere un avviso dalla regola solo dopo un'attenta verifica della sicurezza.  
  
## Vedere anche  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)