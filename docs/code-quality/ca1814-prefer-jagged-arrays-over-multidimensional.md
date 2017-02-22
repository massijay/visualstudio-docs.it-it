---
title: "CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali | Microsoft Docs"
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
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1814: Preferire matrici di matrici rispetto a matrici multidimensionali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Category|Microsoft.Performance|  
|Breaking Change|Breaking|  
  
## Causa  
 Un membro viene dichiarato come matrice multidimensionale.  
  
## Descrizione della regola  
 Una matrice di matrici è una matrice i cui elementi sono costituiti da matrici.  Poiché le matrici che costituiscono gli elementi possono presentare dimensioni diverse, la quantità di spazio inutilizzato sarà inferiore per alcuni insiemi di dati.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare la matrice multidimensionale in una matrice di matrici.  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se la matrice multidimensionale non produce spazio inutilizzato.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrate dichiarazioni per le matrici di matrici e per le matrici multidimensionali.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]