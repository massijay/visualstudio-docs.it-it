---
title: "Procedura: filtrare rapporti tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: filtrare rapporti tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite le opzioni del comando **VSPerfReport** , è possibile filtrare i rapporti in base a un segmento temporale specifico del file dei dati di profilo o limitare i dati a uno o più processi o thread.  Per ulteriori informazioni su questo comando, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**StartTime:**\[*Valore*\]|Mostra soltanto i dati raccolti dopo il valore \(in millisecondi.\)|  
|**EndTime:**\[*Valore*\]|Mostra soltanto i dati raccolti prima del valore \(in millisecondi.\)|  
|**FilterFile:** `VSPFFile`|Specifica il percorso di un file filtro generato dalla finestra **Rapporto di prestazioni di Visual Studio**.|  
|**MsFilter:**\[*OraInizio,Durata*\]|Mostra solo i dati da `StartTime` fino a `Duration` \(in millisecondi\).|  
|**Process:**\[*Pid*\]|Mostra soltanto dati dal processo specificato.|  
|**Thread:**\[*IDThread*\]|Mostra soltanto dati dal thread specificato.|  
|**Thread:**\[*IDThread,IDProcesso*\]|Mostra soltanto i dati dal thread specificato associato al processo specificato.|