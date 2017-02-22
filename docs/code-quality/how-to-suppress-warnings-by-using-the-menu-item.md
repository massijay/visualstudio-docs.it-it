---
title: "Procedura: Eliminare gli avvisi tramite una voce di menu | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "avvisi, eliminazione"
  - "analisi codice, eliminazione di avvisi"
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura: Eliminare gli avvisi tramite una voce di menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  L'eliminazione nell'origine non è supportata per progetti di siti Web.  
  
 È possibile utilizzare la finestra Analisi codice per non visualizzare gli avvisi dell'analisi del codice.  Eliminare un avviso non equivale a disabilitarlo.  La mancata visualizzazione infatti si applica solo a una determinata istanza della violazione.  Altre violazioni dello stesso avviso vengono comunque riportate nella finestra Elenco errori.  
  
 Dopo avere eseguito l'analisi codice, è possibile determinare che uno o più avvisi di analisi del codice visualizzati nella finestra Analisi codice non sono validi per l'applicazione.  È possibile, ad esempio, è possibile determinare che il codice è corretto così com'è.  Talvolta invece vengono rilevate violazioni con priorità bassa che non verranno corrette nel ciclo di sviluppo corrente.  Indipendentemente dal motivo, è spesso utile indicare che l'avviso non è valido in modo da informare i membri del team che è stato esaminato il codice e che è stato stabilito di non visualizzare l'avviso.  L'eliminazione nell'origine è utile in quanto consente di apportare un'eliminazione in corrispondenza della posizione in cui è stato generato l'avviso.  
  
 È possibile scegliere se l'eliminazione apparirà nel codice sorgente o nel file di eliminazione globale.  Alcune eliminazioni devono essere posizionate nel file di eliminazione globale.  Se questo è il caso, l'opzione **In origine** sarà disabilitata.  
  
### Procedura: non visualizzare un avviso utilizzando una voce di menu  
  
1.  Dal menu **Analizza**, scegliere **Windows** e quindi scegliere **Analisi codice**.  
  
2.  Nella finestra **Analisi Codice**, selezionare l'eliminazione dell'avviso.  
  
3.  Selezionare Azioni, quindi scegliere **Elimina messaggio\(i\)**, e quindi scegliere **In origine** o **File di eliminazione in progetto**.  
  
     L'avviso specifico non viene visualizzato e appare barrato nella finestra Analisi codice.  
  
> [!NOTE]
>  Le eliminazioni senza una destinazione vengono visualizzate nel file di eliminazioni globali.