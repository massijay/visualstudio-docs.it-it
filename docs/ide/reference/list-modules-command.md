---
title: "Comando Elenca moduli | Microsoft Docs"
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
  - "debug.listmodules"
helpviewer_keywords: 
  - "Debug.ListModules (comando)"
  - "Elenca moduli (comando)"
  - "ListModules (comando)"
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando Elenca moduli
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Elenca i moduli disponibili per il processo corrente.  
  
## Sintassi  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### Parametri  
 \/Address:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati gli indirizzi di memoria dei moduli.  Il valore predefinito è `yes`.  
  
 \/Name:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati i nomi dei moduli.  Il valore predefinito è `yes`.  
  
 \/Order:`yes|no`  
 Parametro facoltativo.  Specifica se deve essere visualizzato l'ordine dei moduli.  Il valore predefinito è `no`.  
  
 \/Path:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati i percorsi dei moduli..  Il valore predefinito è `yes`.  
  
 \/Process:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati i processi dei moduli.  Il valore predefinito è `no`.  
  
 \/SymbolFile:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati i file dei simboli dei moduli.  Il valore predefinito è `no`.  
  
 \/SymbolStatus:`yes|no`  
 Parametro facoltativo.  Specifica se deve essere visualizzato lo stato dei simboli dei moduli.  Il valore predefinito è `yes`.  
  
 \/Timestamp:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzati i timestamp dei moduli.  Il valore predefinito è `no`.  
  
 \/Version:`yes|no`  
 Parametro facoltativo.  Specifica se devono essere visualizzate le versioni dei moduli.  Il valore predefinito è `no`.  
  
## Note  
  
## Esempio  
 In questo esempio sono indicati i nomi, gli indirizzi e i timestamp dei moduli per il processo corrente.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Procedura: utilizzare la finestra Moduli](../../debugger/how-to-use-the-modules-window.md)