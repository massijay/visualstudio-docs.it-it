---
title: "Comando Elenca origine | Microsoft Docs"
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
  - "Debug.ListSource"
helpviewer_keywords: 
  - "Debug.ListSource (comando)"
  - "Elenca origine (comando)"
  - "ListSource (comando)"
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Elenca origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza le righe del codice sorgente specificate.  
  
## Sintassi  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## Opzioni  
 \/Count:`number`  
 Parametro facoltativo.  Specifica il numero di righe da visualizzare.  
  
 \/Current  
 Parametro facoltativo.  Visualizza la riga corrente.  
  
 \/File:`filename`  
 Parametro facoltativo.  Percorso del file da visualizzare.  Se non viene specificato un nome file, viene visualizzato il codice sorgente per la riga dell'istruzione corrente.  
  
 \/Line:`number`  
 Parametro facoltativo.  Visualizza un numero di riga specifico.  
  
 \/ShowLineNumbers:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati i numeri di riga.  
  
## Note  
  
## Esempio  
 Nell'esempio riportato di seguito, viene mostrato il codice sorgente del file Form1.vb dalla riga 4, con i numeri di riga visibili.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)