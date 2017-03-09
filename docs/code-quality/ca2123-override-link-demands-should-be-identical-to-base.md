---
title: "CA2123: Le richieste di collegamento negli verrine devono essere identiche a quelle nei metodi di base | Microsoft Docs"
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
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123: Le richieste di collegamento negli verrine devono essere identiche a quelle nei metodi di base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo pubblico o protetto in un tipo pubblico esegue l'override di un metodo o implementa un'interfaccia e non presenta la stessa [Link Demands](../Topic/Link%20Demands.md) dell'interfaccia o del metodo virtuale.  
  
## Descrizione della regola  
 Questa regola associa un metodo al relativo metodo di base che può essere un'interfaccia o un metodo virtuale in un altro tipo, quindi confronta le richieste di collegamento in ognuno.  Viene segnalata una violazione se il metodo o il metodo di base presenta una richiesta di collegamento non presente nell'altro metodo.  
  
 Se questa regola viene violata, un chiamante malintenzionato può ignorare la richiesta di collegamento chiamando semplicemente il metodo non sicuro.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, applicare la stessa richiesta di collegamento al metodo o all'implementazione di override.  Se questo non è possibile, contrassegnare il metodo con una richiesta completa o rimuovere insieme l'attributo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate alcune violazioni di questa regola.  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)