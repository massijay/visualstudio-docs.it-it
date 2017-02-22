---
title: "CA2222: Non diminuire la visibilit&#224; di membri ereditati | Microsoft Docs"
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
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2222: Non diminuire la visibilit&#224; di membri ereditati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo privato in un tipo non sealed presenta una firma identica a un metodo pubblico dichiarato in un tipo di base.  Il metodo privato non è finale.  
  
## Descrizione della regola  
 Non modificare il modificatore di accesso per i membri ereditati.  La modifica in privato di un membro ereditato non impedisce ai chiamanti di accedere all'implementazione della classe base del metodo.  Se il membro è reso privato e il tipo è non sealed, i tipi che ereditano possono chiamare l'ultima implementazione pubblica del metodo nella gerarchia di ereditarietà.  Se è necessario modificare il modificatore di accesso, il metodo deve essere contrassegnato come finale oppure il relativo tipo deve essere sealed per impedire che il metodo venga sottoposto a ovverride.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, impostare l'accesso su non privato.  In alternativa, è possibile rendere il metodo finale, purché il linguaggio di programmazione supporti tale operazione.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]