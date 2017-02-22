---
title: "Rapporto Traccia eventi per Windows (ETW) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW (rapporto di profilatura)"
  - "Event Tracing for Windows (rapporto di profilatura)"
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Rapporto Traccia eventi per Windows (ETW)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel rapporto Traccia eventi per Windows \(ETW\) vengono elencati gli eventi ETW registrati in una sessione di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  I dati ETW vengono raccolti in un file binario \(etl\).  
  
> [!NOTE]
>  Non è possibile visualizzare i rapporti ETW nell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Per informazioni sulla raccolta di dati ETW tramite gli strumenti di profilatura dell'interfaccia di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Procedura: Raccogliere dati ETW \(Event Tracing for Windows\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Per informazioni sulla raccolta di dati ETW tramite gli strumenti da riga di comando di [VSPerfCmd](../profiling/vsperfcmd.md), vedere [Eventi](../profiling/events-vsperfcmd.md).  
  
-   Generare il rapporto ETW tramite il comando **\/Summary:ETW** di **VSReport**.  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Timestamp**|Identifica quando si è verificato l'evento.|  
|**ID processo**|Identifica il processo che ha generato l'evento.|  
|**ID thread**|Identifica il thread che ha generato l'evento.|  
|**Descrizione**|Identifica il provider dell'evento.|  
|**Type**|Identifica il tipo di evento.|  
|**Proprietà**|Proprietà dell'evento.  Ogni evento è una coppia nome\-valore delimitata da virgole racchiusa tra parentesi.|