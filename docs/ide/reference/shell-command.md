---
title: "Comando Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - ".exe (file)"
  - "exe (file)"
  - "eseguibili, esecuzione da Visual Studio"
  - "Shell (comando)"
  - "Shell, avvio di file EXE"
  - "Tools.Shell (comando)"
  - "Visual Studio, eseguibili da"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Comando Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avvia programmi eseguibili da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintassi  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## Argomenti  
 `path`  
 Obbligatorio.  Il percorso e il nome del file da eseguire o del documento da aprire.  Se il file specificato non si trova in una delle directory nella variabile di ambiente PATH, è necessario specificare il percorso completo.  
  
 `args`  
 Parametro facoltativo.  Tutti gli argomenti da passare al programma richiamato.  
  
## Opzioni  
 \/commandwindow \[o\] \/command \[o\] \/c \[o\] \/cmd  
 Parametro facoltativo.  Specifica che l'output dell'eseguibile verrà visualizzato nella finestra di **comando**.  
  
 \/dir:`folder` \[o\] \/d: `folder`  
 Parametro facoltativo.  Specifica la directory di lavoro da impostare quando il programma è in esecuzione.  
  
 \/outputwindow \[o\] \/output \[o\] \/out \[o\] \/o  
 Parametro facoltativo.  Specifica che l'output dell'eseguibile verrà visualizzato nella **finestra di output**.  
  
## Note  
 Le opzioni \/dir \/o \/c devono essere specificate immediatamente dopo `Tools.Shell`.  Tutto ciò che viene specificato dopo il nome dell'eseguibile viene passato all'eseguibile come argomento della riga di comando.  
  
 È possibile utilizzare l'alias predefinito `Shell` invece di `Tools.Shell`.  
  
> [!CAUTION]
>  Se nell'argomento `path` sono indicati sia percorso della directory che il nome del file, è consigliabile racchiudere l'intero percorso tra virgolette doppie adiacenti \("""\), come nell'esempio seguente:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Ogni gruppo di tre virgolette doppie \("""\) viene interpretato dal processore `Shell` come un'unica virgoletta doppia.  Nell'esempio precedente, pertanto, al comando `Shell` viene passata la seguente stringa:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Se la stringa non viene racchiusa tra virgolette doppie adiacenti \("""\), in Windows verrà utilizzata solo la porzione di stringa che precede il primo spazio.  Ad esempio, se la stringa utilizzata nell'esempio precedente non viene racchiusa tra virgolette in modo appropriato, verrà cercato un file denominato "Program" memorizzato nella directory radice di C:\\.  Se esiste un file eseguibile C:\\Program.exe, anche se installato con una manomissione non autorizzata, in Windows si tenterà di eseguire questo programma invece del file "c:\\Programmi\\File.exe" desiderato.  
  
## Esempio  
 Il comando riportato di seguito utilizza xcopy.exe per copiare il file `MyText.txt` nella cartella `Text`.  L'output di xcopy.exe viene visualizzato nella **finestra di comando** e nella **finestra di output**.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Finestra di output](../../ide/reference/output-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)