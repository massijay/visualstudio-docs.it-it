---
title: "Comando Print | Microsoft Docs"
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
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print (comando)"
  - "Stampa (comando)"
  - "Print (metodo)"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Print
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Valuta un'espressione o visualizza il testo specificato.  
  
## Sintassi  
  
```  
Debug.Print text  
```  
  
## Argomenti  
 `text`  
 Obbligatorio.  L'espressione da valutare o il testo da visualizzare.  
  
## Note  
 È possibile utilizzare il punto interrogativo \(?\) come alias del comando.  Ad esempio, il comando  
  
```  
>Debug.Print expA  
```  
  
 può essere scritto anche  
  
```  
>? expA  
```  
  
 Entrambe le versioni del comando restituiscono il valore corrente dell'espressione `expA`.  
  
## Esempio  
  
```  
>Debug.Print varA  
```  
  
## Vedere anche  
 [Comando Valuta istruzione](../../ide/reference/evaluate-statement-command.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)