---
title: "Operatore di addizione (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "operatori aritmetici, addizione"
  - "stringhe [Visual Studio], concatenazione"
  - "operatori di concatenazione, confronto con operatore addizione"
  - "addizione (operatori)"
  - "+ (operatore)"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Operatore di addizione (+) (JavaScript)
Somma i valori di due espressioni numeriche o esegue la concatenazione di due stringhe.  
  
## Sintassi  
  
```  
  
result = expression1 + expression2  
```  
  
## Parametri  
 `result`  
 Qualsiasi variabile.  
  
 `expression1`  
 Qualsiasi espressione.  
  
 `expression2`  
 Qualsiasi espressione.  
  
## Note  
 I tipi delle due espressioni determinano il comportamento dell'operatore **\+**.  
  
|Se|Quindi|  
|--------|------------|  
|Entrambe le espressioni sono numeriche o booleane|Aggiungere|  
|Entrambe le espressioni sono stringhe|Concatenare|  
|Un'espressione è numerica e l'altra è una stringa|Concatenare|  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Operatore di assegnazione di addizione \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md)   
 [Riepilogo degli operatori \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)