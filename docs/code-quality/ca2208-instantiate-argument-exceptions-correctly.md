---
title: "CA2208: Creare istanze di eccezioni di argomento correttamente | Microsoft Docs"
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
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2208: Creare istanze di eccezioni di argomento correttamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Fra le possibili cause sono incluse le seguenti situazioni:  
  
-   Viene effettuata una chiamata al costruttore predefinito \(senza parametri\) di un tipo di eccezione che è o deriva da [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True).  
  
-   Un argomento di stringa non corretto viene passato a un costruttore con parametri di un tipo di eccezione che è o che deriva da [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True)  
  
## Descrizione della regola  
 Anziché chiamare il costruttore predefinito, chiamare uno degli overload del costruttore che consenta di fornire un messaggio di eccezione più significativo.  Il messaggio di eccezione deve essere rivolto allo sviluppatore e spiegare chiaramente la condizione di errore e come correggere o evitare l'eccezione.  
  
 Le firme dei primi due costruttori di stringa di <xref:System.ArgumentException> e i relativi tipi derivati non sono coerenti con i parametri `message` e `paramName`.  Accertarsi che questi costruttori siano chiamati con gli argomenti stringa corretti.  Le firme sono le seguenti:  
  
 <xref:System.ArgumentException>\(string `message`\)  
  
 <xref:System.ArgumentException>\(string `message`, string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`, string `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`, string `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`, string `message`\)  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare un costruttore che accetta un messaggio, un nome di parametro o entrambi e assicurarsi che gli argomenti siano adatti al tipo di <xref:System.ArgumentException> da chiamare.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura solo se un costruttore con parametri viene chiamato con gli argomenti stringa corretti.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un costruttore che crea in modo errato un'istanza di un'istanza del tipo ArgumentNullException.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## Esempio  
 Nell'esempio riportato di seguito viene risolta la violazione suddetta scambiando gli argomenti del costruttore.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]