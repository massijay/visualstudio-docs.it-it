---
title: "CA2225: Gli overload degli operatori hanno alternative con nome | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorOverloadsHaveNamedAlternates"
  - "CA2225"
helpviewer_keywords: 
  - "CA2225"
  - "OperatorOverloadsHaveNamedAlternates"
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2225: Gli overload degli operatori hanno alternative con nome
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|Categoria|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 È stato rilevato un overload di operatore e il metodo alternativo denominato previsto non è stato trovato.  
  
## Descrizione della regola  
 L'overload dell'operatore consente di utilizzare simboli per rappresentare calcoli per un tipo.  Ad esempio, un tipo che esegue l'overload del segno più \(\+\) per l'addizione presenta in genere un membro alternativo denominato "Add".  Il membro alternativo denominato fornisce accesso alla stessa funzionalità dell'operatore e viene fornito per gli sviluppatori che programmano in linguaggi che non supportano operatori di overload.  
  
 Questa regola esamina gli operatori elencati nella tabella riportata di seguito.  
  
|C\#|Visual Basic|C\+\+|Nome alternativo|  
|---------|------------------|-----------|----------------------|  
|\+ \(binario\)|\+|\+ \(binario\)|Add|  
|\+\=|\+\=|\+\=|Add|  
|&|And|&|BitwiseAnd|  
|&\=|And\=|&\=|BitwiseAnd|  
|&#124;|Oppure|&#124;|BitwiseOr|  
|&#124;\=|Or\=|&#124;\=|BitwiseOr|  
|\-\-|N\/D|\-\-|Operatore di conversione|  
|\/|\/|\/|Divisione|  
|\/\=|\/\=|\/\=|Divisione|  
|\=\=|\=|\=\=|Equals|  
|^|Xor|^|Xor|  
|^\=|Xor\=|^\=|Xor|  
|\>|\>|\>|Confronto|  
|\>\=|\>\=|\>\=|Confronto|  
|\+\+|N\/D|\+\+|Operatore di incremento|  
|\!\=|\<\>|\!\=|Equals|  
|\<\<|\<\<|\<\<|LeftShift|  
|\<\<\=|\<\<\=|\<\<\=|LeftShift|  
|\<|\<|\<|Confronto|  
|\<\=|\<\=|\<\=|Confronto|  
|&&|N\/D|&&|LogicalAnd|  
|&#124;&#124;|N\/D|&#124;&#124;|LogicalOr|  
|\!|N\/D|\!|LogicalNot|  
|%|Mod|%|Mod o resto|  
|%\=|N\/D|%\=|Mod|  
|\* \(binario\)|\*|\*|Moltiplica|  
|\*\=|N\/D|\*\=|Moltiplica|  
|~|Not|~|OnesComplement|  
|\>\>|\>\>|\>\>|RightShift|  
|\>\>\=|N\/D|\>\>\=|RightShift|  
|\- \(binario\)|\- \(binario\)|\- \(binario\)|Sottrai|  
|\-\=|N\/D|\-\=|Sottrai|  
|true|IsTrue|N\/D|IsTrue \(Proprietà\)|  
|\- \(unario\)|N\/D|\-|Negate|  
|\+ \(unario\)|N\/D|\+|Plus|  
|false|IsFalse|False|IsTrue \(Proprietà\)|  
  
 N\/D \=\= Non può essere sottoposto a overload nel linguaggio selezionato.  
  
 La regola controlla inoltre gli operatori di cast impliciti ed espliciti in un tipo \(`SomeType`\) cercando i metodi denominati `ToSomeType` e `FromSomeType`.  
  
 In C\#, quando si esegue l'overload di un operatore binario, viene eseguito in modo implicito anche l'overload dell'eventuale operatore di assegnazione corrispondente.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, implementare il metodo alternativo per l'operatore; denominarlo utilizzando il nome alternativo consigliato.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola se si implementa una libreria condivisa.  Le applicazioni possono ignorare un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene definita una struttura che viola questa regola.  Per correggere l'esempio, aggiungere un metodo `Add(int x, int y)` pubblico alla struttura.  
  
 [!code-cs[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## Regole correlate  
 [CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: Gli operatori devono avere overload simmetrici](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Eseguire l'override di Equals all'override dell'operatore](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Eseguire l'override di GetHashCode all'override di Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)