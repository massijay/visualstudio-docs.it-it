---
title: "CA1026: Evitare l&#39;utilizzo di parametri predefiniti | Microsoft Docs"
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
  - "CA1026"
  - "DefaultParametersShouldNotBeUsed"
helpviewer_keywords: 
  - "CA1026"
  - "DefaultParametersShouldNotBeUsed"
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1026: Evitare l&#39;utilizzo di parametri predefiniti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo visibile esternamente contiene un metodo visibile esternamente che utilizza un parametro predefinito.  
  
## Descrizione della regola  
 I metodi che utilizzano parametri predefiniti sono consentiti dalla specifica CLS \(Common Language Specification\); questa specifica, tuttavia, consente ai compilatori di ignorare i valori assegnati a questi parametri.  Il codice scritto per compilatori che ignorano i valori dei parametri predefiniti deve fornire in modo esplicito gli argomenti per ogni parametro predefinito.  Per mantenere il comportamento desiderato tra diversi linguaggi di programmazione, è necessario sostituire i metodi che utilizzano parametri predefiniti con overload di metodi che forniscono i parametri predefiniti.  
  
 Il compilatore ignora i valori dei parametri predefiniti per l'Estensione gestita per C\+\+ quando accede al codice gestito.  Il compilatore Visual Basic supporta metodi che dispongono di parametri predefiniti che utilizzano la parola chiave [Optional](/dotnet/visual-basic/language-reference/modifiers/optional).  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il metodo che utilizza parametri predefiniti con overload di metodi che forniscono parametri predefiniti.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che utilizza parametri predefiniti e i metodi di overload che forniscono una funzionalità equivalente.  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## Regole correlate  
 [Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## Vedere anche  
 [Indipendenza del linguaggio e componenti indipendenti dal linguaggio](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)