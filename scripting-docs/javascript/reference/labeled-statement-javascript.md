---
title: "Istruzione con etichetta (JavaScript) | Microsoft Docs"
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
  - "labeled_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "continue (istruzione)"
  - "identificatori, istruzioni"
  - "labeled (istruzione)"
ms.assetid: 019f898e-9e27-4be4-a22f-c5927c7fcae2
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Istruzione con etichetta (JavaScript)
Fornisce un identificatore per un'istruzione.  
  
## Sintassi  
  
```  
  
      label :  
   statements   
```  
  
## Parametri  
 *label*  
 Obbligatorio.  Identificatore univoco utilizzato nei riferimenti all'istruzione con etichetta.  
  
 `statements`  
 Facoltativo.  Una o più istruzioni associate a *label*.  
  
## Note  
 Le etichette vengono utilizzate nelle istruzioni **break** e **continue** per specificare l'istruzione a cui applicare **break** e **continue**.  
  
## Esempio  
 Nel codice seguente l'istruzione **continue** fa riferimento al ciclo **for** preceduto dall'istruzione `Inner:`.  Quando `j` è uguale a 24, l'istruzione **continue** determina il passaggio del ciclo **for** all'iterazione successiva.  I numeri compresi tra 21 e 23 e tra 25 e 30 vengono stampati su ogni riga.  
  
```javascript  
Outer:  
for (i = 1; i <= 10; i++) {  
   document.write ("<br />");  
   document.write ("i: " + i);  
   document.write (" j: ");  
  
Inner:  
   for (j = 21; j <= 30; j++) {  
      if (j == 24)  
          {  
          continue Inner;  
      }  
      document.write (j + " ");  
  }  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Istruzione continue](../../javascript/reference/continue-statement-javascript.md)