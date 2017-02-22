---
title: "CA1715: Gli identificatori devono contenere il prefisso corretto | Microsoft Docs"
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
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1715: Gli identificatori devono contenere il prefisso corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Category|Microsoft.Naming|  
|Breaking Change|Sostanziale \- Quando generato su interfacce<br /><br /> Non sostanziale – Se generato su parametri di tipo generici.|  
  
## Causa  
 Il nome di un'interfaccia visibile esternamente non inizia con una "I" maiuscola.  
  
 In alternativa  
  
 Il nome di un parametro di tipo generico su un tipo o metodo visibile esternamente non inizia con una "T" maiuscola.  
  
## Descrizione della regola  
 Per convenzione i nomi di determinati elementi di programmazione iniziano con un prefisso specifico.  
  
 I nomi di interfaccia devono iniziare con la I maiuscola seguita da un'altra lettera maiuscola.  Questa regola riporta violazioni per i nomi di interfaccia quali "MyInterface" e "IsolatedInterface".  
  
 I nomi di parametri di tipo generico devono iniziare con una "T" maiuscola facoltativamente seguita da un'altra lettera maiuscola.  Questa regola segnala violazioni per i nomi di parametri di tipo generici quali "V" e "Type".  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Rinominare l'identificatore in modo che presenti il prefisso corretto.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 **Nell'esempio riportato di seguito viene illustrata un'interfaccia denominata in modo errato.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## Esempio  
 **Nell'esempio riportato di seguito viene risolta la violazione precedente mediante l'aggiunta del prefisso 'I' al nome dell'interfaccia.**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## Esempio  
 **Nell'esempio riportato di seguito viene illustrato un parametro di tipo generico denominato in modo errato.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]  
  
## Esempio  
 **Nell'esempio riportato di seguito viene risolta la violazione precedente aggiungendo il prefisso 'T' al nome del parametro di tipo generico.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]  
  
## Regole correlate  
 [CA1722: Gli identificatori non devono contenere il prefisso non corretto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)