---
title: "CA2214: Non chiamare metodi sottoponibili a override nei costruttori | Microsoft Docs"
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
  - "DoNotCallOverridableMethodsInConstructors"
  - "CA2214"
helpviewer_keywords: 
  - "CA2214"
  - "DoNotCallOverridableMethodsInConstructors"
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2214: Non chiamare metodi sottoponibili a override nei costruttori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCallOverridableMethodsInConstructors|  
|CheckId|CA2214|  
|Categoria|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Il costruttore di un tipo non sealed chiama un metodo virtuale definito nella relativa classe.  
  
## Descrizione della regola  
 Quando viene chiamato un metodo virtuale, il tipo effettivo che esegue il metodo non viene selezionato fino alla fase di esecuzione.  Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, non chiamare i metodi virtuali di un tipo dall'interno dei costruttori del tipo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  Il costruttore deve essere riprogettato per eliminare la chiamata al metodo virtuale.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'effetto della violazione di questa regola.  L'applicazione di test crea un'istanza di `DerivedType` che causa l'esecuzione del costruttore della relativa classe base \(`BadlyConstructedType`\).  Il costruttore di `BadlyConstructedType` chiama erroneamente il metodo virtuale `DoSomething`.  Come illustrato nell'output, viene eseguito `DerivedType.DoSomething()` prima dell'esecuzione del costruttore di `DerivedType`.  
  
 [!code-cs[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]  
  
 Questo esempio produce l'output che segue.  
  
  **Calling base ctor.**  
**Derived DoSomething is called \- initialized ?  No**  
**Calling derived ctor.**