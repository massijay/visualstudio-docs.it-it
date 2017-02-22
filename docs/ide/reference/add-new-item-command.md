---
title: "Comando Aggiungi nuovo elemento | Microsoft Docs"
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
  - "project.addnewitem"
helpviewer_keywords: 
  - "Aggiungi nuovo elemento (comando)"
  - "File.AddNewItem (comando)"
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Aggiunge un nuovo elemento di soluzione, quale un file HTM, CSS o TXT o una pagina con frame, alla soluzione corrente e lo apre.  
  
## Sintassi  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## Argomenti  
 `filename`  
 Parametro facoltativo.  Il percorso e il nome di file dell'elemento da aggiungere alla soluzione.  
  
## Opzioni  
 \/t: `templatename`  
 Parametro facoltativo.  Specifica il tipo di file da creare.  Se non viene fornito alcun modello, per impostazione predefinita viene creato un file di testo.  
  
 La sintassi dell'argomento \/t:`templatename` riflette le informazioni riportate nella finestra di dialogo **Aggiungi nuovo elemento di soluzione**.  è necessario immettere il nome completo della categoria e il tipo di file separati da una barra rovesciata \(`\`\), racchiudendo l'intera stringa tra virgolette.  
  
 Se ad esempio si desidera creare un nuovo file di testo, per l'argomento \/t:`templatename`, è necessario immettere quanto segue.  
  
```  
/t:"General\Style Sheet"  
```  
  
 \/e: `editorname`  
 Parametro facoltativo.  Il nome dell'editor in cui verrà aperto il file.  Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.  
  
 La sintassi dell'argomento \/e:`editorname` utilizza i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette.  
  
 Se ad esempio si desidera aprire un foglio di stile nell'editor del codice sorgente, per l'argomento \/e:`editorname`, è necessario immettere quanto segue.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Esempio  
 Nell'esempio riportato di seguito, un nuovo elemento di soluzione, denominato MyHTMLpg, viene aggiunto alla soluzione corrente.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)