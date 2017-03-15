---
title: "CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 I nomi di due tipi, membri, parametri o spazi dei nomi completi sono identici quando vengono convertiti in lettere minuscole.  
  
## Descrizione della regola  
 Gli identificatori per spazi dei nomi, tipi, membri e parametri non possono differire solo in base a maiuscole e minuscole poiché ai linguaggi destinati a Common Language Runtime non è richiesta la distinzione tra maiuscole e minuscole.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ad esempio, è un linguaggio senza distinzione tra maiuscole e minuscole ampiamente utilizzato.  
  
 Questa regola funziona solo su membri pubblicamente visibili.  
  
## Come correggere le violazioni  
 Scegliere un nome che sia univoco se confrontato con altri identificatori senza distinzione tra maiuscole e minuscole.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  La libreria potrebbe non essere utilizzabile in tutti i linguaggi disponibili in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Esempio di una violazione  
 Nell'esempio riportato di seguito viene illustrata una violazione di questa regola.  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## Regole correlate  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)