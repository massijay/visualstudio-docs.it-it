---
title: "Comando Watch | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.watch"
helpviewer_keywords: 
  - "Debug.Watch (comando)"
  - "Espressioni di controllo (comando)"
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Watch
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea e apre un'istanza specificata di una finestra **Espressioni di controllo**.  La finestra **Espressioni di controllo** può essere utilizzata per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.  
  
## Sintassi  
  
```  
Debug.Watch[index]  
```  
  
## Argomenti  
 `index`  
 Obbligatorio.  Il numero di istanza della finestra Espressioni di controllo.  
  
## Note  
 `index` deve essere un Integer.  I valori validi sono 1, 2, 3 o 4.  
  
## Esempio  
  
```  
>Debug.Watch1  
```  
  
## Vedere anche  
 [Finestre Auto e Variabili locali](../../debugger/autos-and-locals-windows.md)   
 [Procedura: modificare un valore in una finestra variabili](../Topic/How%20to:%20Edit%20a%20Value%20in%20a%20Variable%20Window.md)   
 [Procedura: utilizzare la finestra di dialogo Controllo immediato](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)