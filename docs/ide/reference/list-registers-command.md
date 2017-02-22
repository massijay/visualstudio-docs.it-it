---
title: "Comando Elenca registri | Microsoft Docs"
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
  - "debug.listregisters"
helpviewer_keywords: 
  - "Debug.ListRegisters (comando)"
  - "Elenca registri (comando)"
  - "ListRegisters (comando)"
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Elenca registri
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza il valore dei registri selezionati e consente di modificare l'elenco dei registri da visualizzare.  
  
## Sintassi  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## Opzioni  
 \/Display \[{`register`&#124;`registerGroup`}...\]  
 Visualizza il valore del parametro `register` o `registerGroup` specificato.  Se non è stato specificato un parametro `register` o `registerGroup`, viene visualizzato l'elenco dei registri predefinito.  Se non viene specificata un'opzione, il comportamento è lo stesso.  Di seguito è riportato un esempio:  
  
 `Debug.ListRegisters /Display eax`  
  
 equivale a  
  
 `Debug.ListRegisters eax`  
  
 \/List  
 Visualizza tutti i gruppi di registri dell'elenco.  
  
 \/Watch \[{`register`&#124;`registerGroup`}...\]  
 Aggiunge uno o più valori di `register` o `registerGroup` all'elenco.  
  
 \/Unwatch \[{`register`&#124;`registerGroup`}...\]  
 Rimuove uno o più valori di `register` o `registerGroup` dall'elenco.  
  
## Note  
 È possibile utilizzare l'alias `r` invece di `Debug.ListRegisters`.  
  
## Esempio  
 Nell'esempio viene utilizzato l'alias `r` di `Debug.ListRegisters` per visualizzare il valore del gruppo di registri `Flags`.  
  
```  
r /Display Flags  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Nozioni fondamentali di debug: finestra Registri](../../debugger/debugging-basics-registers-window.md)   
 [Procedura: utilizzare la finestra Registri](../../debugger/how-to-use-the-registers-window.md)