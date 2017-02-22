---
title: "Comando Controllo immediato | Microsoft Docs"
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
  - "debug.quickwatch"
helpviewer_keywords: 
  - "Debug.Quickwatch (comando)"
  - "Controllo immediato (comando)"
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Controllo immediato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza il testo selezionato o specificato nel campo Espressione della [finestra di dialogo Controllo immediato](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md).  È possibile utilizzare questa finestra di dialogo per calcolare il valore corrente di una variabile o di un'espressione riconosciuta dal debugger oppure il contenuto di un registro.  È possibile inoltre modificare il valore di qualsiasi variabile non costante oppure il contenuto di qualsiasi registro.  
  
## Sintassi  
  
```  
Debug.QuickWatchq [text]  
```  
  
## Argomenti  
 `text`  
 Parametro facoltativo.  Il testo da aggiungere alla finestra di dialogo **Controllo immediato**.  
  
## Note  
 Se l'argomento `text` viene omesso, alla finestra Espressioni di controllo viene aggiunto il testo selezionato o la parola in corrispondenza del cursore.  
  
## Esempio  
  
```  
>Debug.QuickWatch  
```  
  
## Vedere anche  
 [Procedura: utilizzare la finestra di dialogo Controllo immediato](../Topic/How%20to:%20Use%20the%20QuickWatch%20Dialog%20Box.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)