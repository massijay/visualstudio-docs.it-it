---
title: "CA1506: Evitare un numero eccessivo di accoppiamenti di classi | Microsoft Docs"
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
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
helpviewer_keywords: 
  - "AvoidExcessiveClassCoupling"
  - "CA1506"
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1506: Evitare un numero eccessivo di accoppiamenti di classi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveClassCoupling|  
|CheckId|CA1506|  
|Category|Microsoft.Maintainability|  
|Breaking Change|Breaking|  
  
## Causa  
 Un tipo o metodo è accoppiato con molti altri tipi.  
  
## Descrizione della regola  
 Questa regola misura l'accoppiamento tra classi contando il numero di riferimenti al tipo univoci contenuti in un tipo o metodo.  
  
 Tipi e metodi con un alto livello di accoppiamento tra classi possono risultare difficili da gestire.  È buona norma fare in modo che tipi e metodi presentino un basso livello di accoppiamento e un'alta coesione.  
  
## Come correggere le violazioni  
 Per correggere questa violazione, tentare di riprogettare il tipo o metodo per ridurre il numero di tipi a cui è accoppiato.  
  
## Esclusione di avvisi  
 Escludere questo avviso quando il tipo o metodo è considerato accettabile, nonostante il numero elevato di dipendenze su altri tipi.  
  
## Vedere anche  
 [Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)   
 [Misurazione della complessità e della manutenibilità del codice gestito](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)