---
title: "CA1900: I campi dei tipi di valore devono essere portabili | Microsoft Docs"
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
  - "CA1900"
  - "ValueTypeFieldsShouldBePortable"
helpviewer_keywords: 
  - "ValueTypeFieldsShouldBePortable"
  - "CA1900"
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1900: I campi dei tipi di valore devono essere portabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|Category|Microsoft.Portability|  
|Breaking Change|Sostanziale: se il campo è visibile all'esterno dell'assembly.<br /><br /> Non sostanziale \- Se il campo non è visibile all'esterno dell'assembly.|  
  
## Causa  
 Questa regola consente di verificare che le strutture dichiarate con layout esplicito vengano allineate correttamente quando viene eseguito il marshalling a codice non gestito nei sistemi operativi a 64 bit.  IA\-64 non consente accessi di memoria non allineata e, se la violazione non viene corretta, il processo verrà arrestato.  
  
## Descrizione della regola  
 Le strutture con layout esplicito contenente campi non allineati determinano arresti del sistema nel sistema operativo a 64 bit.  
  
## Come correggere le violazioni  
 Tutti i campi di dimensioni inferiori a 8 byte devono avere offset che siano multipli della relativa dimensione, mentre i campi di 8 byte o superiori devono avere offset multipli di 8.  Un'altra soluzione è utilizzare `LayoutKind.Sequential` anziché `LayoutKind.Explicit`, se adeguato.  
  
## Esclusione di avvisi  
 Il presente avviso dovrà essere escluso solo se si verifica in caso di errore.