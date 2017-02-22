---
title: "Comando Imposta/Rimuovi punto di interruzione | Microsoft Docs"
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
  - "debug.togglebreakpoint"
helpviewer_keywords: 
  - "Debug.ToggleBreakPoint (comando)"
  - "Imposta/Rimuovi punto di interruzione (comando)"
  - "ToggleBreakpoint (comando)"
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Imposta/Rimuovi punto di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta o rimuove il punto di interruzione, a seconda dello stato corrente, nella posizione corrente all'interno del file.  
  
## Sintassi  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## Argomenti  
 `text`  
 Parametro facoltativo.  Se viene specificato un testo, la riga viene contrassegnata come un punto di interruzione denominato.  In caso contrario, la riga viene contrassegnata come un punto di interruzione senza nome, analogamente a quanto si verifica quando si preme F9.  
  
## Esempio  
 Nell'esempio seguente viene impostato\/rimosso il punto di interruzione corrente.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)