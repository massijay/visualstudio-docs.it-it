---
title: "Comando Vai a | Microsoft Docs"
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
  - "edit.goto"
helpviewer_keywords: 
  - "Debug.Goto (comando)"
  - "Vai a (comando)"
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Vai a
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sposta il cursore sulla riga specificata.  
  
## Sintassi  
  
```  
Edit.GoTo [linenumber]  
```  
  
## Argomenti  
 `linenumber`  
 Parametro facoltativo.  Un Integer che rappresenta il numero della riga su cui deve essere spostato il cursore.  
  
## Note  
 La numerazione delle righe inizia da uno.  Se il valore di `linenumber` è inferiore a uno, viene visualizzata la prima riga.  Se il valore di `linenumber` è superiore al numero corrispondente all'ultima riga, viene visualizzata l'ultima riga.  
  
 Se per `linenumber` non viene specificato alcun valore, viene visualizzata la finestra di dialogo **Vai alla riga**.  
  
 L'alias per questo comando è GoToLn.  
  
## Esempio  
  
```  
>Edit.GoTo 125  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)