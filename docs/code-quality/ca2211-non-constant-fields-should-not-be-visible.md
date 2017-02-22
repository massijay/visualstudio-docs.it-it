---
title: "CA2211: I campi non costanti non devono essere visibili | Microsoft Docs"
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
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2211: I campi non costanti non devono essere visibili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## Causa  
 Un campo statico pubblico o protetto non è costante né in sola lettura.  
  
## Descrizione della regola  
 I campi statici che non sono costanti né in sola lettura non sono thread\-safe.  L'accesso a tali campi deve essere controllato attentamente e richiede tecniche di programmazione avanzate per la sincronizzazione dell'accesso all'oggetto classe.  Poiché si tratta di competenze di difficile apprendimento e insegnamento e il test di tale oggetto presenta difficoltà, è consigliabile utilizzare i campi statici per archiviare dati non soggetti a modifica.  Questa regola si applica alle librerie, mentre le applicazioni non devono esporre alcun campo.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, rendere costante o di sola lettura il campo statico.  Se questa operazione non è possibile, riprogettare il tipo in modo che utilizzi un meccanismo alternativo quale una proprietà thread\-safe che gestisca l'accesso thread\-safe al campo sottostante.  Tenere presente che problemi quali conflitti di blocco e deadlock possono incidere sulle prestazioni e sul comportamento della libreria.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura se si sta sviluppando un'applicazione e pertanto si dispone del controllo completo sull'accesso al tipo che contiene il campo statico.  È oppotuno che i progettisti di librerie non escludano un avviso da questa regola. L'utilizzo di campi statici non costanti può rendere difficile il corretto utilizzo della libreria da parte degli sviluppatori.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un tipo che viola questa regola.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]