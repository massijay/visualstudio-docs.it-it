---
title: "Non &#232; possibile ereditare l&#39;interfaccia &#39;&lt;nomeinterfaccia1&gt;&#39; perch&#233; potrebbe essere identica all&#39;interfaccia &#39;&lt;nomeinterfaccia2&gt;&#39; da cui eredita l&#39;interfaccia &#39;&lt;nomeinterfaccia3&gt;&#39; per alcuni argomenti di tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32123"
  - "vbc32123"
helpviewer_keywords: 
  - "BC32123"
ms.assetid: 2b8fa1f0-3d43-45c6-99d0-328151479b43
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Non &#232; possibile ereditare l&#39;interfaccia &#39;&lt;nomeinterfaccia1&gt;&#39; perch&#233; potrebbe essere identica all&#39;interfaccia &#39;&lt;nomeinterfaccia2&gt;&#39; da cui eredita l&#39;interfaccia &#39;&lt;nomeinterfaccia3&gt;&#39; per alcuni argomenti di tipo
Un'interfaccia generica eredita da due o più interfacce generiche e due delle ereditarietà potrebbero essere in conflitto per determinati valori di argomenti di tipo.  
  
 Le istruzioni seguenti possono generare questo errore.  
  
```  
Public Interface interfaceA(Of u) End Interface Public Interface interfaceX(Of v) Inherits interfaceA(Of v) End Interface Public Interface derivedInterface(Of t1, t2) Inherits interfaceA(Of t1), interfaceX(Of t2) End Interface  
```  
  
 Se l'interfaccia `derivedInterface` è costruita o implementata specificando lo stesso tipo sia in `t1` che in `t2`, deve ereditare due versioni di `interfaceA` con argomenti di tipo identici. In questo modo si produrrebbe un'ambiguità sulla versione a cui accedere.  
  
 **ID errore:** BC32123  
  
### Per correggere l'errore  
  
-   Modificare uno degli argomenti di tipo forniti all'interfaccia derivata in modo che non siano presenti conflitti.  
  
     \-oppure\-  
  
-   Rimuovere dall'istruzione `Inherits` una delle interfacce che determina il potenziale conflitto di ereditarietà o implementazione.  
  
## Vedere anche  
 [NOT IN BUILD: Cenni preliminari sulle interfacce](http://msdn.microsoft.com/it-it/f96bb470-c1b8-4c73-89bc-6f536b798da1)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Tipi generici in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)