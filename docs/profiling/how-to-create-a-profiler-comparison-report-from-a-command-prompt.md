---
title: "Procedura: creare un rapporto di confronto del profiler da un prompt dei comandi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Procedura: creare un rapporto di confronto del profiler da un prompt dei comandi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile generare un rapporto degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per il confronto dei dati di prestazioni di due file dei dati di profilo \(con estensione VSP o VSPS\).  Nel rapporto vengono mostrate le differenze, le regressioni delle prestazioni e i miglioramenti riscontrati tra una sessione di profilo e un'altra.  I valori del rapporto indicano la variazione \(delta\) rispetto alla linea di base del primo file specificato.  Il valore delta viene calcolato determinando la differenza tra il valore precedente, ovvero il valore della linea di base, e il valore risultante dalla nuova analisi.  I confronti di dati del profiler possono essere basati sulle funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione \(IP\) e tipi.  
  
 Per elencare gli identificatori dei campi e delle categorie di confronto, digitare la riga di comando seguente:  
  
 **VSPerfReport \/querydifftables**  *VspFileName1* *VspFileName2*  
  
 Per creare il rapporto di confronto, utilizzare la sintassi seguente:  
  
 **VSPerfReport \/diff**  `VspFileName1` *VspFileName2* \[**\/**`Options`\]  
  
 È possibile aggiungere le opzioni contenute nella tabella seguente alla riga di comando **VSPerfReport \/diff** .  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**DiffThreshold:**\[*Valore*\]|Ignorare la differenza se è inferiore a questo valore soglia percentuale.  I nuovi dati con valori inferiori a questa soglia non verranno visualizzati.|  
|**DiffTable:** *NomeTabella*|Utilizzare questa tabella per confrontare i file.  Per impostazione predefinita, viene utilizzata la tabella delle funzioni.  Specificare l'identificatore elencato in **VSPerfReport \/querydifftables**.|  
|**DiffColumn:** *NomeColonna*|Utilizzare questa colonna per confrontare i valori.  Per impostazione predefinita, viene utilizzata la colonna delle percentuali di campioni esclusivi.  Specificare l'identificatore elencato in **VSPerfReport \/querydifftables**.|