---
title: "CA2122: Non esporre in modo indiretto metodi con richieste di collegamento | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122: Non esporre in modo indiretto metodi con richieste di collegamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Category|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro pubblico o protetto presenta un [Link Demands](../Topic/Link%20Demands.md) ed è chiamato da un membro che non esegue alcun controllo della sicurezza.  
  
## Descrizione della regola  
 Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato.  Se un membro `X` non effettua richieste di sicurezza dei relativi chiamanti e chiama codice protetto da una richiesta di collegamento, un chiamante privo dell'autorizzazione necessaria potrà utilizzare `X` per accedere al membro protetto.  
  
## Come correggere le violazioni  
 Aggiungere un [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) di sicurezza o una richiesta di collegamento al membro in modo che non fornisca più accesso non protetto al membro protetto dalla richiesta di collegamento.  
  
## Esclusione di avvisi  
 Per escludere in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non conceda ai chiamanti l'accesso a operazioni o risorse che possono essere utilizzate in modo distruttivo.  
  
## Esempio  
 Negli esempi riportati di seguito vengono illustrate una libreria che viola la regola e un'applicazione che mette in evidenza i punti deboli della libreria.  Nella libreria di esempio sono contenuti due metodi che insieme violano la regola.  Il metodo `EnvironmentSetting` è protetto da una richiesta di collegamento per l'accesso illimitato alle variabili di ambiente.  Il metodo `DomainInformation` non effettua richieste di sicurezza dei relativi chiamanti prima di chiamare `EnvironmentSetting`.  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## Esempio  
 L'applicazione riportata di seguito chiama il membro della libreria non protetto.  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Valore da membro non protetto: seattle.corp.contoso.com**   
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)