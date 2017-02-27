---
title: "Comando Registra output finestra di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.logcommandwindowoutput"
helpviewer_keywords: 
  - "Registra output finestra di comando (comando)"
  - "View.LogCommandWindowOutput (comando)"
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Comando Registra output finestra di comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Copia interamente l'input e l'output della finestra di **comando** in un file.  
  
## Sintassi  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## Argomenti  
 `filename`  
 Parametro facoltativo.  Il nome del file di log.  Per impostazione predefinita, il file viene creato nella cartella del profilo utente.  Se il nome di file esiste già, il log viene aggiunto alla fine del file esistente.  Se non viene specificato alcun file, viene utilizzato l'ultimo file specificato.  Se non esiste alcun file precedente, viene creato un file di log predefinito, denominato cmdline.log.  
  
> [!TIP]
>  Per modificare il percorso in cui viene salvato il file di log, immettere il percorso completo del file, racchiuso tra virgolette se contiene degli spazi.  
  
## Opzioni  
 \/on  
 Parametro facoltativo.  Avvia la registrazione per la finestra di **comando** nel file di log specificato e accoda al file le nuove informazioni.  
  
 \/off  
 Parametro facoltativo.  Interrompe la registrazione per la finestra di **comando**.  
  
 \/overwrite  
 Parametro facoltativo.  Se il file specificato nell'argomento `filename` corrisponde a un file esistente, tale file viene sovrascritto.  
  
## Note  
 Se non viene specificato alcun file, per impostazione predefinita viene creato il file cmdline.log.  Per impostazione predefinita, l'alias per questo comando è Log.  
  
## Esempi  
 Nell'esempio riportato di seguito viene creato il nuovo file di log cmdlog e viene avviata la registrazione dei comandi.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Nell'esempio seguente viene interrotta la registrazione dei comandi.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 In quest'ultimo esempio viene ripresa la registrazione dei comandi nel file di log precedentemente utilizzato.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)