---
title: "Comando Aggiungi elemento esistente | Microsoft Docs"
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
  - "project.addexistingitem"
helpviewer_keywords: 
  - "Aggiungi elemento esistente (comando)"
  - "File.AddExistingItem (comando)"
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Aggiungi elemento esistente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Aggiunge un file esistente alla soluzione corrente e lo apre.  
  
## Sintassi  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## Argomenti  
 `filename`  
 Obbligatorio.  Il percorso completo e il nome di file con estensione dell'elemento da aggiungere alla soluzione corrente.  Se il percorso o il nome di file contiene degli spazi, l'intero percorso deve essere racchiuso tra virgolette.  
  
## Opzioni  
 \/e: `editorname`  
 Parametro facoltativo.  Il nome dell'editor in cui verrà aperto il file.  Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.  
  
 La sintassi dell'argomento \/e:`editorname` utilizza i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette.  Se ad esempio si desidera aprire un foglio di stile nell'editor del codice sorgente, per l'argomento \/e:`editorname`, è necessario immettere quanto segue.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Note  
 La funzionalità di completamento automatico tenta di individuare il percorso e il nome di file corretti durante la digitazione.  
  
## Esempio  
 Nell'esempio riportato di seguito, il file Form1.frm viene aggiunto alla soluzione corrente.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)