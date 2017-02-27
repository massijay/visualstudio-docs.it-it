---
title: "Procedura: configurare le regole di prestazioni degli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.ruleseditor"
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: configurare le regole di prestazioni degli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di prestazioni degli strumenti di profilatura di Visual Studio segnalano i problemi che possono rallentare l'esecuzione di un'applicazione profilata.  Gli avvisi possono anche indicare la necessità di modificare i metodi di raccolta per raccogliere dati più utili.  Gli avvisi di prestazione vengono generati automaticamente in una sessione di profilatura e visualizzati nella finestra **Elenco errori** quando un file dei dati di profilatura viene aperto in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Certi avvisi potrebbero non essere validi per gli scenari desiderati e alcuni potrebbero essere generati in modo non corretto.  È possibile configurare gli avvisi di prestazioni per visualizzare o nascondere avvisi specifici.  
  
### Per configurare avvisi di prestazione del profiler  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Strumenti di prestazioni**, quindi fare clic su **Regole**.  
  
3.  Per abilitare o disabilitare un avviso, selezionare o deselezionare la casella di controllo accanto al nome e all'**ID** dell'avviso.  
  
4.  Per specificare il livello di avviso di una regola, fare clic sulla cella **Azione** accanto alla regola, quindi fare clic sul livello di avviso.  
  
    -   **Disabilitato** \- Disabilita la regola ed equivale a deselezionare la casella di controllo accanto all'ID regola.  
  
    -   **Avviso** \- Visualizza la regola come avviso.  
  
    -   **Errore** \- Interrompe l'esecuzione della profilatura e visualizza la regola come errore.  
  
    -   **Informazioni** \- Visualizza la regola solo a scopo informativo.