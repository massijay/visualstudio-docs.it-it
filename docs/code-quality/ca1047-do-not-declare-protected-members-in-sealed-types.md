---
title: "CA1047: Non dichiarare membri protetti nei tipi sealed | Microsoft Docs"
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
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1047: Non dichiarare membri protetti nei tipi sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo pubblico è `sealed` \(`NotInheritable` in Visual Basic\) e dichiara un membro protetto o un tipo annidato protetto.  Questa regola non segnala violazioni per i metodi <xref:System.Object.Finalize%2A> che devono seguire questo modello.  
  
## Descrizione della regola  
 I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override.  Per definizione, non è possibile ereditare da un tipo sealed, pertanto non è possibile chiamare metodi protetti su tipi sealed.  
  
 Il compilatore C\# genera un avviso per questo errore.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il livello di accesso del membro in privato oppure rendere ereditabile il tipo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Se si lascia il tipo nello stato corrente è possibile causare problemi di gestione e non ottenere alcun vantaggio.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]