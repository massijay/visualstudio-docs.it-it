---
title: "CA1716: Gli identificatori non devono corrispondere a parole chiave | Microsoft Docs"
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
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1716: Gli identificatori non devono corrispondere a parole chiave
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Un nome di uno spazio dei nomi, un tipo o un membro virtuale o di interfaccia corrisponde a una parola chiave riservata in un linguaggio di programmazione.  
  
## Descrizione della regola  
 Gli identificatori di spazi dei nomi, tipi e membri virtuali e di interfaccia non devono corrispondere a parole chiave definite dai linguaggi destinati a Common Language Runtime.  A seconda del linguaggio in uso e della parola chiave, errori del compilatore e ambiguità possono rendere difficoltoso l'utilizzo della libreria.  
  
 Questa regola effettua verifiche in base a parole chiave per i seguenti linguaggi:  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 Per le parole chiave di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] viene effettuato un confronto senza distinzione tra maiuscole e minuscole, mentre per gli altri linguaggi viene utilizzato il confronto con distinzione tra maiuscole e minuscole.  
  
## Come correggere le violazioni  
 Selezionare un nome non contenuto nell'elenco delle parole chiave.  
  
## Esclusione di avvisi  
 È possibile eliminare un avviso per questa regola in caso di certezza che l'identificatore non venga confuso con gli utenti delle API e che la libreria è utilizzabile in tutte le lingue disponibili in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].