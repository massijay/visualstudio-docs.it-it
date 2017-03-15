---
title: "Comando Imposta radice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.setradix"
helpviewer_keywords: 
  - "Debug.SetRadix (comando)"
  - "Imposta radice (comando)"
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Comando Imposta radice
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta o restituisce la base numerica utilizzata per visualizzare gli Integer.  
  
## Sintassi  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## Argomenti  
 `10` o `16`, `hex` o `dec`  
 Parametro facoltativo.  Indica un valore decimale \(10 o dec\) o esadecimale \(16 o hex\).  Se l'argomento viene omesso, viene restituito il valore della radice corrente.  
  
## Esempio  
 Nell'esempio che segue, l'ambiente viene impostato per la visualizzazione degli Integer in formato esadecimale.  
  
```  
>Debug.SetRadix hex  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)