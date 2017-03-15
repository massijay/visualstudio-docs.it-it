---
title: "Comando Elenca memoria | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listmemory"
helpviewer_keywords: 
  - "Debug.ListMemory (comando)"
  - "Elenca memoria (comando)"
  - "ListMemory (comando)"
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Comando Elenca memoria
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza il contenuto dell'intervallo di memoria specificato.  
  
## Sintassi  
  
```  
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]  
[/Hex|Signed|Unsigned] [expression]  
```  
  
## Argomenti  
 `expression`  
 Parametro facoltativo.  L'indirizzo di memoria a partire dal quale inizia la visualizzazione della memoria.  
  
## Opzioni  
 \/ANSI&#124;Unicode  
 Parametro facoltativo.  Visualizza la memoria sotto forma di caratteri corrispondenti ai byte di memoria, in formato ANSI o Unicode.  
  
 \/Count:`number`  
 Parametro facoltativo.  Determina il numero di byte di memoria da visualizzare a partire da `expression`.  
  
 \/Format:`formattype`  
 Parametro facoltativo.  Il tipo di formato da utilizzare per visualizzare le informazioni della memoria nella finestra **Memoria**. Può corrispondere a OneByte, TwoBytes, FourBytes, EightBytes, Float \(32 bit\) o Double \(64 bit\).  Se viene utilizzato il formato OneByte, l'opzione `/Unicode` non è disponibile.  
  
 \/Hex&#124;Signed&#124;Unsigned  
 Parametro facoltativo.  Specifica il formato da utilizzare per visualizzare i numeri: con segno, senza segno o esadecimale.  
  
## Note  
 Anziché scrivere un comando **Debug.ListMemory** completo con tutte le opzioni, per determinate opzioni preimpostate su valori specifici è possibile richiamare il comando utilizzando alias predefiniti.  Ad esempio, anziché immettere:  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
 è possibile scrivere:  
  
```  
>df /Count:30 /Unicode  
```  
  
 Di seguito viene riportato l'elenco degli alias disponibili per il comando **Debug.ListMemory**:  
  
|Alias|Comandi e opzioni|  
|-----------|-----------------------|  
|**d**|Debug.ListMemory|  
|**da**|Debug.ListMemory \/Ansi|  
|**db**|Debug.ListMemory \/Format:OneByte|  
|**dc**|Debug.ListMemory \/Format:FourBytes \/Ansi|  
|**dd**|Debug.ListMemory \/Format:FourBytes|  
|**df**|Debug.ListMemory\/Format:Float|  
|**dq**|Debug.ListMemory \/Format:EightBytes|  
|**du**|Debug.ListMemory \/Unicode|  
  
## Esempio  
  
```  
>Debug.ListMemory /Format:float /Count:30 /Unicode  
```  
  
## Vedere anche  
 [Comando Elenca stack di chiamate](../../ide/reference/list-call-stack-command.md)   
 [Comando Elenca thread](../../ide/reference/list-threads-command.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)