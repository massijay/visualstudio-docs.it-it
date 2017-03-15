---
title: "Procedura: creare un rapporto ETW degli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Procedura: creare un rapporto ETW degli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel rapporto Traccia eventi per Windows \(ETW\) vengono elencati gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  I dati ETW vengono raccolti in un file binario \(etl\).  Per ulteriori informazioni su questo rapporto, vedere [Rapporto Traccia eventi per Windows \(ETW\)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Non è possibile visualizzare i rapporti ETW nell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Per informazioni sulla raccolta di dati ETW tramite l'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Procedura: Raccogliere dati ETW \(Event Tracing for Windows\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Per informazioni sulla raccolta di dati ETW da un prompt dei comandi, vedere [VSPerfCmd](../profiling/vsperfcmd.md) e [Eventi](../profiling/events-vsperfcmd.md).  
  
 Generare il rapporto ETW tramite il comando **\/summary:etw** di **VSReport**.  Il file con estensione etl che contiene i dati ETW deve essere nella stessa directory del file dei dati di profilo \(vsp o vsps\).  Per impostazione predefinita, il rapporto viene generato come file con valori separati da virgole \(csv\).  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
### Per generare un rapporto ETW  
  
-   Nella finestra del **Prompt dei comandi** digitare la riga di comando seguente:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/Summary:ETW \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Il percorso degli strumenti di profilatura.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|File dei dati di profilatura \(con estensione vsp o vsps\).  Sono accettati i percorsi completi e parziali.|  
    |Xml|Genera un rapporto formattato in XML.|