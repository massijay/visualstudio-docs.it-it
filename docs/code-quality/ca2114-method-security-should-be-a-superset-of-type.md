---
title: "CA2114: La sicurezza del metodo deve essere un superset del tipo | Microsoft Docs"
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
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114: La sicurezza del metodo deve essere un superset del tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo presenta sicurezza dichiarativa e uno dei relativi metodi presenta sicurezza dichiarativa per la stessa azione di sicurezza la quale non è [Link Demands](../Topic/Link%20Demands.md) o [Inheritance Demands](http://msdn.microsoft.com/it-it/28b9adbb-8f08-4f10-b856-dbf59eb932d9). Inoltre, le autorizzazioni controllate dal tipo non sono un sottoinsieme delle autorizzazioni controllate dal metodo.  
  
## Descrizione della regola  
 Un metodo non deve presentare sicurezza dichiarativa sia a livello di metodo che a livello di tipo per la stessa azione.  I due controlli non sono combinati; viene applicata solo la richiesta a livello di metodo.  Se, ad esempio, un tipo richiede l'autorizzazione `X` e uno dei relativi metodi richiede l'autorizzazione `Y`, il codice non necessita dell'autorizzazione `X` per eseguire il metodo.  
  
## Come correggere le violazioni  
 Rivedere il codice per assicurarsi che entrambe le azioni siano necessarie.  Se entrambe le azioni sono necessarie, assicurarsi che l'azione a livello di metodo includa la sicurezza specificata a livello di tipo.  Se ad esempio il tipo richiede l'autorizzazione `X` e il relativo metodo deve anche richiedere l'autorizzazione `Y`, il metodo deve richiedere esplicitamente sia `X` che `Y`.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se il metodo non richiede la sicurezza specificata dal tipo.  Si tratta, tuttavia, di uno scenario non comune che può indicare l'esigenza di un'accurata revisione della progettazione.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono utilizzate autorizzazioni di accesso all'ambiente per illustrare i rischi derivanti dalla violazione di questa regola.  Nell'esempio, il codice dell'applicazione crea un'istanza del tipo protetto prima di negare l'autorizzazione richiesta dal tipo.  In un caso reale di rischio, l'applicazione richiederebbe un altro modo per ottenere un'istanza dell'oggetto.  
  
 Nell'esempio riportato di seguito, la libreria richiede l'autorizzazione di scrittura per un tipo e l'autorizzazione di lettura per un metodo.  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## Esempio  
 Il codice dell'applicazione riportato di seguito dimostra la vulnerabilità della libreria chiamando il metodo anche se non soddisfa il requisito di sicurezza a livello di tipo.  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **\[Tutte le autorizzazioni\] Informazioni personali: 6\/16\/1964 12:00:00 AM \[Nessuna autorizzazione di scrittura \(richieste dal tipo\)\] Informazioni personali: 6\/16\/1964 12:00:00 AM \[Nessuna autorizzazione di lettura \(richiesta dal metodo\)\] Impossibile accedere alle informazioni personali: richiesta non riuscita.**   
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/it-it/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)