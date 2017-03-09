---
title: "CA2134: I metodi devono conservare trasparenza consistente durante l&#39;override dei metodi base | Microsoft Docs"
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
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134: I metodi devono conservare trasparenza consistente durante l&#39;override dei metodi base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Questa regola funziona quando un metodo contrassegnato con <xref:System.Security.SecurityCriticalAttribute> esegue l'override di un metodo trasparente o contrassegnato con <xref:System.Security.SecuritySafeCriticalAttribute>.  La regola funziona anche quando un metodo che è trasparente o contrassegnato da <xref:System.Security.SecuritySafeCriticalAttribute> esegue l'override di un metodo contrassegnato con <xref:System.Security.SecurityCriticalAttribute>.  
  
 La regola è applicata in caso di esecuzione dell'override di un metodo virtuale o di implementazione di un'interfaccia.  
  
## Descrizione della regola  
 Questa regola funziona su tentativi di modificare l'accessibilità di sicurezza di un metodo più distante sulla catena di ereditarietà.  Ad esempio, se un metodo virtuale in una classe di base è trasparente o SafeCrtical, la classe derivata deve eseguire l'override  con un metodo trasparente o SafeCritical.  Viceversa, se SecurityCritical virtuale, la classe derivata deve eseguire l'override con un metodo SecurityCritical.  La stessa regola si applica per l'implementazione dei metodi di interfaccia.  
  
 Le regole di trasparenza sono applicate quando il codice è compilato tramite JIT anziché in fase di esecuzione, in modo che il calcolo della trasparenza non dispone di informazioni dinamiche sul tipo.  Pertanto, il risultato del calcolo della trasparenza deve poter essere determinato soltanto dai tipi statici che sono stati compilati tramite JIT, indipendentemente dal tipo dinamico.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la trasparenza del metodo che sta eseguendo l'override di un metodo virtuale o sta implementando un'interfaccia per mettere in corrispondenza la trasparenza del metodo di interfaccia o virtuale.  
  
## Esclusione di avvisi  
 Non escludere gli avvisi da questa regola.  Violazioni di questa regola comporteranno un runtime <xref:System.TypeLoadException> per assembly che utilizzano trasparenza di livello 2.  
  
## Esempi  
  
### Codice  
 [!CODE [FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency#1)]  
  
## Vedere anche  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)