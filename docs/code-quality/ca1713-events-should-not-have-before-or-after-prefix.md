---
title: "CA1713: Non utilizzare il prefisso Before o After negli eventi | Microsoft Docs"
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
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1713: Non utilizzare il prefisso Before o After negli eventi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un evento inizia con "Before" o "After".  
  
## Descrizione della regola  
 I nomi degli eventi devono descrivere l'azione che genera l'evento.  Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni.  Ad esempio, quando si denomina una coppia di eventi generati alla chiusura di una risorsa, è possibile denominarli "Closing" e "Closed" anziché "BeforeClose" e "AfterClose".  
  
 Le convenzioni di denominazione forniscono un aspetto comune alle librerie che si avvalgono di Common Language Runtime.  In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e i clienti possono confidare nel fatto che la libreria è stata sviluppata da un esperto nello sviluppo di codice gestito.  
  
## Come correggere le violazioni  
 Rimuovere il prefisso dal nome dell'evento e provare a modificare il nome utilizzando i tempi presente o passato di un verbo.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.