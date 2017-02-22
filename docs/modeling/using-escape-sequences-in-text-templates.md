---
title: "Using Escape Sequences in Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, escape sequences"
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Using Escape Sequences in Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare sequenze di escape nei modelli di testo per generare tag di modello di testo e \(solo in codice C\#\) per utilizzare caratteri di escape per i caratteri di controllo e le virgolette.  
  
 Per stampare i tag di apertura e chiusura per un blocco di codice standard in un file di output, utilizzare caratteri di escape per i tag come segue:  
  
```  
\<# ... \#>  
```  
  
 È possibile seguire la stessa procedura con gli altri tag di direttiva del modello di testo e i tag del blocco di codice.  
  
 Se un blocco di testo include stringhe utilizzate per applicare caratteri di escape ai tag del modello di testo, è possibile utilizzare le sequenze di escape seguenti:  
  
-   Se un tag del modello di testo viene preceduto da un numero pari di caratteri di escape \(\\\), il parser del modello includerà metà dei caratteri di escape e includerà la sequenza come tag del modello di testo.  Ad esempio, se nel modello di testo vi sono quattro caratteri di escape, nel file generato saranno presenti due caratteri "\\".  
  
-   Se un tag del modello di testo viene preceduto da un numero dispari di caratteri di escape \(\\\), il parser del modello includerà metà dei caratteri "\\" più il tag stesso \(\<\# o \#\>\).  Questo tag non viene considerato come un tag del modello di testo.  
  
-   Se un carattere di escape \(\\\) appare in una qualsiasi altra posizione in una sequenza diversa da dove sono utilizzati caratteri di escape per un carattere di controllo o una virgoletta \(solo in C\#\), il carattere sarà restituito direttamente.  
  
## Vedere anche  
 [How to: Generate Templates from Templates By Using Escape Sequences](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)