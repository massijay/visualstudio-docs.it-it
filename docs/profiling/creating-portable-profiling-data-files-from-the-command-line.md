---
title: "Creazione di file dei dati di profilatura portabili tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Creazione di file dei dati di profilatura portabili tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per semplificare la condivisione dei dati di profilo, è possibile utilizzare lo strumento da riga di comando [VSPerfReport](../profiling/vsperfreport.md) per incorporare i simboli per un'esecuzione del profilo nel file vsp.  
  
 È inoltre possibile creare un file dei dati di profilo pre\-analizzato con estensione vsps di dimensioni inferiori e più facilmente caricabile nell'IDE.  
  
> [!NOTE]
>  Assicurarsi che i file di simboli \(pdb\) siano disponibili per **VSPerfReport**.  Per ulteriori informazioni, vedere [Procedura: specificare percorsi dei file di simboli tramite la riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Per informazioni sul percorso di **VSReport**, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  I dati di profilo contenuti in un file vsps non possono essere filtrati.  
  
### Per incorporare i simboli per un'esecuzione del profilo in un file dei dati di profilo \(vsp\)  
  
-   Nella finestra del prompt dei comandi digitare il comando seguente:  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/PackSymbols**  
  
     Per impostazione predefinita, il nome del file vsps corrisponde al nome di base del file vsp.  È possibile specificare un nome alternativo utilizzando l'opzione **Output**.  
  
### Per creare un file dei dati di profilo di riepilogo  
  
-   Nella finestra del prompt dei comandi digitare il comando seguente:  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/SummaryFile** \[**\/Output:**\<File Name\>\]  
  
     Per impostazione predefinita, il nome del file vsps corrisponde al nome di base del file vsp.  È possibile specificare un nome alternativo utilizzando l'opzione **Output**.