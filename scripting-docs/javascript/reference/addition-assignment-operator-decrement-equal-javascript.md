---
title: "Operatore di assegnazione di addizione (+=) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operatore di assegnazione di addizione (+=)"
  - "+= (operatore)"
  - "operatori di assegnazione, JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Operatore di assegnazione di addizione (+=) (JavaScript)
Aggiunge il valore di un'espressione al valore di una variabile e assegna il risultato alla variabile.  
  
## Sintassi  
  
```  
  
result += expression   
```  
  
## Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression`  
 Qualsiasi espressione.  
  
## Note  
 Utilizzare questo operatore equivale esattamente a specificare: `result = result + expression`.  
  
 I tipi delle due espressioni determinano il comportamento dell'operatore `+=`.  
  
|Se|Quindi|  
|--------|------------|  
|Entrambe le espressioni sono numeriche o booleane|Aggiungere|  
|Entrambe le espressioni sono stringhe|Concatenare|  
|Un'espressione è numerica e l'altra è una stringa|Concatenare|  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore addizione \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)