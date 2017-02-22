---
title: "Comando Nuovo file | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "file.newfile"
helpviewer_keywords: 
  - "File.NewFile (comando)"
  - "Nuovo file (comando)"
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Nuovo file
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un nuovo file e lo apre.  Il file viene visualizzato nella cartella File esterni.  
  
## Sintassi  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## Argomenti  
 `filename`  
 Parametro facoltativo.  Il nome del file.  Se non viene specificato alcun nome, viene fornito un nome predefinito.  Se non viene indicato alcun nome di modello, viene creato un file di testo.  
  
## Opzioni  
 \/t:`templatename`  
 Parametro facoltativo.  Specifica il tipo di file da creare.  
  
 \/t: la sintassi dell' argomento di`templatename` riflettono le informazioni contenute nella nuova finestra di dialogo dei File.  Immettere il nome della categoria seguito da una barra rovesciata \(`\`\) e il nome del modello, quindi racchiudere l'intera stringa tra virgolette.  
  
 Se ad esempio si desidera creare un nuovo file di origine [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], per l'argomento \/t:`templatename`, è necessario immettere quanto segue.  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 L'esempio sopra riportato indica che il modello del file di C\+\+ è incluso nella categoria Visual C\+\+ nella finestra di dialogo **Nuovo file**.  
  
 \/e:`editorname`  
 Parametro facoltativo.  Il nome dell'editor in cui verrà aperto il file.  Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.  
  
 \/e: la sintassi dell' argomento di`editorname` utilizza i nomi dell' editor come sono visualizzati voce con la finestra di dialogo, racchiusi tra virgolette.  
  
 Se ad esempio si desidera aprire un file nell'editor del codice sorgente, per l'argomento \/e:`editorname`, è necessario immettere quanto segue.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## Esempio  
 Nell'esempio riportato di seguito viene creata e aperta nell'editor del codice sorgente una nuova pagina Web denominata "test1.htm".  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Finestra di controllo immediato](../../ide/reference/immediate-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)