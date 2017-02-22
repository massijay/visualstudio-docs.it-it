---
title: "CA1721: I nomi delle propriet&#224; non devono corrispondere ai metodi get | Microsoft Docs"
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
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721: I nomi delle propriet&#224; non devono corrispondere ai metodi get
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un membro pubblico o protetto inizia con "Get" e per il resto corrisponde al nome di una proprietà pubblica o protetta.  Ad esempio, un tipo che contiene un metodo denominato "GetColor" e una proprietà denominata "Color" viola questa regola.  
  
## Descrizione della regola  
 I metodi Get e le proprietà devono avere nomi indicano chiaramente la distinzione tra le loro funzioni.  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo, si riduce il tempo necessario per l'apprendimento di una nuova libreria software e i clienti possono confidare nel fatto che la libreria sia stata sviluppata da esperti nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Modificare il nome in modo che non corrisponda al nome di un metodo con prefisso "Get".  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
> [!NOTE]
>  È possibile escludere questo avviso se il metodo Get è causato dall'implementazione dell'interfaccia IExtenderProvider.  
  
## Esempio  
 Nell'esempio riportato di seguito sono contenuti un metodo e una proprietà che violano questa regola.  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## Regole correlate  
 [CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)