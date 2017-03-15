---
title: "CA2103: Controllare la sicurezza imperativa | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103: Controllare la sicurezza imperativa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo utilizza la sicurezza imperativa e potrebbe costruire l'autorizzazione tramite le informazioni sullo stato o i valori restituiti che possono essere modificati mentre la richiesta è attiva.  
  
## Descrizione della regola  
 La sicurezza imperativa utilizza oggetti gestiti per specificare autorizzazioni e azioni di sicurezza durante l'esecuzione del codice, a differenza della sicurezza dichiarativa che utilizza attributi per archiviare autorizzazioni e azioni in metadati.  La sicurezza imperativa è estremamente flessibile poiché è possibile impostare lo stato di un oggetto autorizzazioni e selezionare azioni di sicurezza utilizzando informazioni non disponibili fino alla fase di esecuzione.  Tale flessibilità comporta il rischio che le informazioni della fase di runtime utilizzate per determinare lo stato di un'autorizzazione non rimangano invariate mentre l'azione è in corso.  
  
 Utilizzare la sicurezza dichiarativa quando possibile.  Le richieste dichiarative sono più semplici da comprendere.  
  
## Come correggere le violazioni  
 Rivedere le richieste di sicurezza imperative per verificare che lo stato dell'autorizzazione non si basi su informazioni che possono essere modificate mentre l'autorizzazione è in uso.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è un'operazione sicura se l'autorizzazione non è basata sulla modifica di dati.  È, tuttavia, preferibile modificare la richiesta imperativa nel relativo equivalente dichiarativo.  
  
## Vedere anche  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)