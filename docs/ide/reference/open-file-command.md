---
title: "Comando Apri file | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.openfile"
helpviewer_keywords: 
  - "File.OpenFile (comando)"
  - "of (comando)"
  - "Apri file (comando)"
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Comando Apri file
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Apre un file esistente e consente di specificare un editor.  
  
## Sintassi  
  
```  
File.OpenFile filename [/e:editorname]  
```  
  
## Argomenti  
 `filename`  
 Obbligatorio.  Il percorso completo o parziale e il nome del file da aprire.  I percorsi contenenti spazi devono essere racchiusi tra virgolette.  
  
## Opzioni  
 \/e:`editorname`  
 Parametro facoltativo.  Il nome dell'editor in cui verrà aperto il file.  Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.  
  
 \/e: la sintassi dell' argomento di`editorname` utilizza i nomi dell' editor come sono visualizzati voce con la finestra di dialogo, racchiusi tra virgolette.  
  
 Se ad esempio si desidera aprire un file nell'editor del codice sorgente, per l'argomento \/e:`editorname`, è necessario immettere quanto segue.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Note  
 Quando si immette un percorso, la funzionalità di completamento automatico tenta di individuare il percorso e il nome di file corretti.  
  
## Esempio  
 Nell'esempio riportato di seguito viene aperto il file di stile "Test1.css" nell'editor del codice sorgente.  
  
```  
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Finestra di controllo immediato](../../ide/reference/immediate-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)