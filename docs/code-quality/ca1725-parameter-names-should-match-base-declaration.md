---
title: "CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base | Microsoft Docs"
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
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un parametro in un override di un metodo visibile esternamente non corrisponde al nome del parametro nella dichiarazione di base o nella dichiarazione di interfaccia del metodo.  
  
## Descrizione della regola  
 Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo.  Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il parametro in modo che corrisponda alla dichiarazione di base.  La correzione è una modifica importante per i metodi visibili a COM.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola se non per i metodi visibili a COM rilasciati in precedenza.