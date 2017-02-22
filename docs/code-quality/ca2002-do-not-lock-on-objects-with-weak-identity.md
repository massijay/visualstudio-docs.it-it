---
title: "CA2002: Non bloccare oggetti con identit&#224; debole | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotLockOnObjectsWithWeakIdentity"
  - "CA2002"
helpviewer_keywords: 
  - "CA2002"
  - "DoNotLockOnObjectsWithWeakIdentity"
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2002: Non bloccare oggetti con identit&#224; debole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotLockOnObjectsWithWeakIdentity|  
|CheckId|CA2002|  
|Category|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un thread tenta di acquisire un blocco su un oggetto con identità debole.  
  
## Descrizione della regola  
 Un oggetto presenta un'identità debole quando è possibile accedere ad esso direttamente attraverso i confini dei domini applicazione.  Un thread che tenta di acquisire un blocco su un oggetto con identità debole può essere bloccato da un secondo thread in un altro dominio applicazione con un blocco sullo stesso oggetto.  I tipi riportati di seguito presentano identità debole e sono contrassegnati dalla regola:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, utilizzare un oggetto di un tipo non contenuto nell'elenco riportato nella sezione Descrizione.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Regole correlate  
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati alcuni blocchi di oggetti che violano la regola.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-cs[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## Vedere anche  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [Istruzione lock](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)