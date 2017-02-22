---
title: "CA2147: Il codice Transparent non pu&#242; utilizzare asserzioni di sicurezza | Microsoft Docs"
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
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2147: Il codice Transparent non pu&#242; utilizzare asserzioni di sicurezza
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Al codice contrassegnato come <xref:System.Security.SecurityTransparentAttribute> non sono concesse autorizzazioni sufficienti per l'asserzione.  
  
## Descrizione della regola  
 Questa regola analizza tutti i metodi e i tipi in un assembly interamente Security Transparent o una combinazione di Security Transparent e Security Critical e contrassegna l'utilizzo dichiarativo o imperativo di <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 In fase di esecuzione, qualsiasi chiamata a <xref:System.Security.CodeAccessPermission.Assert%2A> da codice Security Transparent causerà la generazione di un'eccezione <xref:System.InvalidOperationException>.  Tale situazione può verificarsi sia negli assembly interamente Security Transparent sia negli assembly che sono una combinazione di Security Transparent e Security Critical in cui un metodo o un tipo è dichiarato trasparente, ma include un'asserzione dichiarativa o imperativa.  
  
 Con [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 è stata introdotta una funzionalità denominata *trasparenza*.  I singoli metodi, campi, interfacce, classi e tipi possono essere o trasparenti o critici.  
  
 Il codice trasparente non ha accesso a privilegi di sicurezza avanzati.  Pertanto, qualsiasi autorizzazione venga concessa o richiesta tramite tale codice viene automaticamente passata attraverso il codice al chiamante o al dominio dell'applicazione host.  Sono esempi di possibili elevazioni le asserzioni, le pretese LinkDemand, l'attributo SuppressUnmanagedCode e il codice `unsafe`.  
  
## Come correggere le violazioni  
 Per risolvere il problema, contrassegnare il codice che chiama l'asserzione con <xref:System.Security.SecurityCriticalAttribute> o rimuovere l'asserzione.  
  
## Esclusione di avvisi  
 Non sopprimere un messaggio da questa regola.  
  
## Esempio  
 Il codice non verrà eseguito correttamente se `SecurityTestClass` è trasparente, quando il metodo `Assert` genera una <xref:System.InvalidOperationException>.  
  
 [!code-cs[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## Esempio  
 Nell'esempio riportato di seguito, un'opzione consiste nel rivedere il codice del metodo SecurityTransparentMethod e se il metodo è considerato sicuro per l'elevazione, contrassegnare SecurityTransparentMethod come critico per la sicurezza. Ciò richiede che un controllo di sicurezza, senza errori, completo e dettagliato venga eseguito sul metodo insieme a qualsiasi callout che si verifica all'interno del metodo sotto l'asserzione:  
  
 [!code-cs[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 Un'altra opzione consiste nel rimuovere l'asserzione dal codice e lasciare che le richieste di autorizzazione di I\/O del file successive vengano passate da SecurityTransparentMethod al chiamante.  Abilita i controlli di sicurezza.  In genere, in questi casi non è necessario alcun controllo di sicurezza, poiché le richieste di autorizzazione passeranno al chiamante e\/o al dominio dell'applicazione.  Le richieste di autorizzazione sono controllate rigorosamente tramite la concessione di autorizzazioni relative ai criteri di sicurezza, all'ambiente host e al codice sorgente.  
  
## Vedere anche  
 [Avvisi di sicurezza](../code-quality/security-warnings.md)