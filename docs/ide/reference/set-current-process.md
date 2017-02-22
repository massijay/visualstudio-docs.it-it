---
title: "Imposta processo corrente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comando Debug.SetCurrentProcess"
  - "comando Imposta processo corrente"
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Imposta processo corrente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta il processo specificato come processo attivo nel debugger.  
  
## Sintassi  
  
```  
Debug.SetCurrentProcess index  
```  
  
## Argomenti  
 `index`  
 Obbligatorio.  L'indice del processo.  
  
## Note  
 Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo per volta.  Per impostare il processo attivo, è possibile utilizzare il comando `SetCurrentProcess`.  
  
## Esempio  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)