---
title: "Procedura: Creare un rapporto calltrace degli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW [Visual Studio ALM], visualizzazione di dati"
  - "strumenti di prestazioni, visualizzazione dati ETW"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: Creare un rapporto calltrace degli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il *rapporto calltrace* per gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contiene informazioni di intervallo per ciascun punto di ingresso e di uscita delle funzioni dell'applicazione e ciascuna chiamata eseguita dalla funzione ad altre funzioni.  I rapporti calltrace sono disponibili solo per i dati di profilatura se raccolti con il metodo di strumentazione.  
  
> [!NOTE]
>  Non è possibile visualizzare i rapporti calltrace in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  È necessario utilizzare lo strumento da riga di comando **VSPerfReport** per generare un valore delimitato da virgole \(.csv\) o un file XML.  Per ulteriori informazioni su questo strumento, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
### Per creare un rapporto calltrace  
  
1.  Aprire una finestra del **prompt dei comandi**.  
  
2.  Al prompt dei comandi digitare il seguente comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Il percorso degli strumenti da riga di comando disponibili negli strumenti di profilatura.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|File dei dati di profilatura \(con estensione vsp o vsps\).  Sono accettati i percorsi completi e parziali.|  
    |Xml|Genera un rapporto in formato XML.|  
  
## Vedere anche  
 [Procedura: Raccogliere dati ETW \(Event Tracing for Windows\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API per strumenti di profilatura](../profiling/profiling-tools-apis.md)