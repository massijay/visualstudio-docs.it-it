---
title: "Comando Percorso simboli | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.symbolpath"
helpviewer_keywords: 
  - "Debug.SymbolPath (comando)"
  - "Percorso simboli (comando)"
  - "SymbolPath (comando)"
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Comando Percorso simboli
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli.  
  
## Sintassi  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## Argomenti  
 `pathname`  
 Opzionale.  Elenco di percorsi delimitato da punti e virgola in cui il debugger deve eseguire la ricerca dei simboli.  
  
## Note  
 Se non viene specificato un `pathname`, viene visualizzato l'elenco dei percorsi simboli correnti.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono aggiunti due percorsi all'elenco delle directory di simboli.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene visualizzato l'elenco delimitato da punti e virgola dei percorsi simboli correnti.  
  
```  
Debug.SymbolPath  
```  
  
## Vedere anche  
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)