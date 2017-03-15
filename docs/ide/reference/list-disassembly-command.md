---
title: "Comando Elenca disassembly | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly (comando)"
  - "Elenca disassembly (comando)"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Comando Elenca disassembly
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avvia il processo di debug e consente di specificare come devono essere gestiti gli errori.  
  
## Sintassi  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## Opzioni  
 Ciascuna opzione può essere richiamata utilizzando la forma completa o una forma abbreviata.  
  
 \/count: `number` \[o\] \/c: `number` \[o\] \/length: `number` \[o\] \/l: `number`  
 Parametro facoltativo.  Il numero di istruzioni da visualizzare.  Il valore predefinito è 8.  
  
 \/endaddress: `expression` \[o\] \/e: `expression`  
 Parametro facoltativo.  L'indirizzo in cui deve essere interrotto il disassembly.  
  
 \/codebytes:`yes`&#124;`no` \[o\] \/bytes:`yes`&#124;`no` \[o\] \/b:`yes`&#124;`no`  
 Parametro facoltativo.  Indica se devono essere visualizzati i byte del codice.  Il valore predefinito è `no`.  
  
 \/source:`yes`&#124;`no` \[o\] \/s:`yes`&#124;`no`  
 Parametro facoltativo.  Indica se deve essere visualizzato il codice sorgente.  Il valore predefinito è `no`.  
  
 \/symbolnames:`yes`&#124;`no` \[o\] \/names:`yes`&#124;`no` \[o\] \/n:`yes`&#124;`no`  
 Parametro facoltativo.  Indica se devono essere visualizzati i nomi dei simboli.  Il valore predefinito è `yes`.  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 Parametro facoltativo.  Abilita la visualizzazione dei numeri di riga associati al codice sorgente.  Per utilizzare l'opzione \/linenumbers, il valore dell'opzione \/source deve essere `yes`.  
  
## Esempio  
  
```  
>Debug.ListDisassembly  
```  
  
## Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca thread](../../ide/reference/list-threads-command.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)