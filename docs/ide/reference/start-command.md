---
title: "Comando Avvia | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.start"
helpviewer_keywords: 
  - "Debug.Start (comando)"
  - "Avvia (comando)"
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Comando Avvia
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avvia il debug del progetto di avvio.  
  
## Sintassi  
  
```  
Debug.Start [address]  
```  
  
## Argomenti  
 `address`  
 Parametro facoltativo.  L'indirizzo al quale viene sospesa l'esecuzione, analogamente al punto di interruzione nel codice sorgente.  Questo argomento è valido solo nella modalità di debug.  
  
## Note  
 Eseguendo il comando **Start**, viene eseguita un'operazione RunToCursor all'indirizzo specificato.  
  
## Esempio  
 Nell'esempio riportato di seguito viene avviato il debugger e vengono ignorate tutte le eccezioni generate.  
  
```  
>Debug.Start  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)