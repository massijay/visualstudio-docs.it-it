---
title: "CA1053: I tipi che contengono membri statici non devono avere costruttori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1053: I tipi che contengono membri statici non devono avere costruttori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto.  
  
## Descrizione della regola  
 Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo.  Poiché il tipo non presenta membri non statici, la creazione di un'istanza non consente di accedere ad alcun membro del tipo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere il costruttore predefinito o renderlo privato.  
  
> [!NOTE]
>  Alcuni compilatori creano automaticamente un costruttore predefinito pubblico se il tipo non definisce alcun costruttore.  In questo caso, aggiungere un costruttore predefinito privato per eliminare la violazione.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  La presenza del costruttore indica che il tipo non è un tipo statico.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  Si noti che non è presente alcun costruttore predefinito nel codice sorgente.  Quando questo codice viene compilato in un assembly, il compilatore C\# inserirà un costruttore predefinito, con conseguente violazione della regola.  Per correggere il problema, dichiarare un costruttore privato.  
  
 [!CODE [FxCop.Design.StaticTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes#1)]