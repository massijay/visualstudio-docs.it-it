---
title: "CA1030: Utilizzare eventi dove appropriato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseEventsWhereAppropriate"
  - "CA1030"
helpviewer_keywords: 
  - "CA1030"
  - "UseEventsWhereAppropriate"
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1030: Utilizzare eventi dove appropriato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un nome di metodo pubblico, protetto o privato inizia con uno dei seguenti elementi:  
  
-   AddOn  
  
-   RemoveOn  
  
-   Fire  
  
-   Raise  
  
## Descrizione della regola  
 Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi.  Gli eventi seguono il modello di progettazione Observer o Publish\-Subscribe, sono utilizzati quando una modifica dello stato in un oggetto deve essere comunicata ad altri oggetti.  Se un metodo viene chiamato in risposta a una modifica dello stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi.  Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.  
  
 Alcuni esempi comuni di eventi si trovano nelle applicazioni di interfaccia utente in cui un'azione dell'utente quale la scelta di un pulsante causa l'esecuzione di un segmento di codice.  Il modello di evento [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] non si limita alle interfacce utente, deve essere utilizzato ogni volta che è necessario comunicare modifiche dello stato a uno o più oggetti.  
  
## Come correggere le violazioni  
 Se il metodo viene chiamato quando lo stato di un oggetto viene modificato, è opportuno provare a modificare la progettazione in modo da utilizzare il modello di evento [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola se il metodo non funziona con il modello eventi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].