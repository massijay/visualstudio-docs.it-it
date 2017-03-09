---
title: "Esempio Dia2dump | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "applicazioni di esempio [DIA SDK]"
  - "Esempio Dia2dump [DIA SDK]"
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Esempio Dia2dump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio di Dia2dump viene installato con Visual Studio e contiene il file di origine di Dia2dump.cpp.  Le esecuzioni compilate in eseguibile dalla riga di comando e le visualizzazioni che il contenuto dell'intero database di programma \(PDB\) viene memorizzato.  
  
### Per installare l'esempio  
  
1.  Verificare che il sistema soddisfi tutte le richieste di installazione descritte nella pagina iniziale di installazione di Visual Studio.  
  
2.  Installare Visual Studio e seguire le istruzioni di installazione e di configurazione per gli esempi inclusi.  
  
#### Per compilare l'esempio  
  
1.  aprire il file di Dia2dump.sln in Visual Studio.  \(Se necessario, Visual Studio innanzitutto consentirà di migliorare il progetto di Dia2dump\).  
  
2.  Nelle pagine delle proprietà del progetto, in **C\/C\+\+** &#124; **Generale** &#124; **directory di inclusione aggiuntive** la proprietà, specifica  `. \DIA SDK \ include` directory.  In questo modo si garantisce che il compilatore possibile trovare il file di dia2.h.  
  
3.  Scegliere **Ricompila soluzione** dal menu **Compila**.  
  
4.  chiudere Visual Studio.  
  
#### Per eseguire l’esempio  
  
1.  Aprire un prompt dei comandi e digitare quanto segue:  
  
    ```  
    dia2dump filename  
    ```  
  
## Vedere anche  
 [File di origine Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)