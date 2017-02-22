---
title: "CA1050: Dichiarare i tipi negli spazi dei nomi | Microsoft Docs"
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
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1050: Dichiarare i tipi negli spazi dei nomi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo pubblico o protetto viene definito all'esterno dell'ambito di uno spazio dei nomi denominato.  
  
## Descrizione della regola  
 I tipi vengono dichiarati all'interno degli spazi dei nomi per impedire conflitti di denominazione e per organizzare i tipi correlati in una gerarchia di oggetti.  I tipi all'esterno di qualsiasi spazio dei nomi denominato sono contenuti in uno spazio dei nomi globale a cui non è possibile fare riferimento nel codice.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, inserire il tipo in uno spazio dei nomi.  
  
## Esclusione di avvisi  
 Sebbene non sia mai necessario escludere un avviso da questa regola, questa esclusione è sicura se l'assembly non verrà mai utilizzato con altri assembly.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata una libreria con un tipo dichiarato in modo errato all'esterno di uno spazio dei nomi e un tipo con lo stesso nome dichiarato in uno spazio dei nomi.  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## Esempio  
 Nell'applicazione riportata di seguito viene utilizzata la libreria definita in precedenza.  Si noti che il tipo dichiarato all'esterno di uno spazio dei nomi viene creato quando il nome `Test` non è qualificato da uno spazio dei nomi.  Si noti inoltre che per accedere al tipo `Test` in `Goodspace`, è necessario disporre del nome dello spazio dei nomi.  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]