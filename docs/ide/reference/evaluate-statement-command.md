---
title: "Comando Valuta istruzione | Microsoft Docs"
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
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement (comando)"
  - "Valuta istruzione (comando)"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Valuta istruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Valuta e visualizza l'istruzione specificata.  
  
## Sintassi  
  
```  
Debug.EvaluateStatement text   
```  
  
## Argomenti  
 `text`  
 Obbligatorio.  L'istruzione da valutare.  
  
## Note  
 La finestra utilizzata per immettere il comando **EvaluateStatement** determina se il segno di uguale \(\=\) deve essere interpretato come operatore di confronto o operatore di assegnazione.  
  
 Nella finestra **Comando**, il segno uguale \(\=\) viene interpretato come operatore di confronto.  Pertanto, se, ad esempio, i valori delle variabili `a` e `b` sono diversi, il comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 restituisce il valore `false`.  
  
 Nella finestra di **Controllo immediato**, invece, il segno uguale \(\=\) viene interpretato come operatore di assegnazione.  Ad esempio, il comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 ad esempio assegna alla variabile `a` il valore della variabile `b`.  
  
## Esempio  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## Vedere anche  
 [Comando Print](../../ide/reference/print-command.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)