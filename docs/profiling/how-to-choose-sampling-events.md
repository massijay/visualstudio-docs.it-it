---
title: "Procedura: Scegliere eventi di campionamento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.sampling"
helpviewer_keywords: 
  - "cicli di clock (evento di esempio)"
  - "eventi di esempio, scelta"
  - "strumenti per la profilatura, eventi di esempio"
  - "errori di pagina (evento di esempio)"
  - "chiamata di sistema (evento di esempio)"
  - "contatore di prestazioni (evento di esempio)"
  - "strumenti per le prestazioni, eventi di esempio"
ms.assetid: ce7cb734-80ac-4930-a4ef-e24395e1cc07
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: Scegliere eventi di campionamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] raccolgono dati di prestazioni a un intervallo specificato come numero di cicli del processore utilizzati dal processo profilato.  Il numero predefinito di cicli in un intervallo è 10.000.000, che è di circa 0,01 secondi su un computer ad 1 GHZ.  È possibile modificare il numero di cicli in un intervallo e anche l'evento di esempio.  Sono disponibili gli eventi di esempio riportati di seguito.  
  
-   Cicli di clock per i problemi legati alla CPU .  
  
-   Errori di pagina per i problemi relativi alla memoria.  
  
-   Chiamate di sistema per i problemi associati all'I\/O.  
  
-   Contatore di prestazioni, ovvero contatori CPU per problemi di prestazioni ridotte.  
  
> [!IMPORTANT]
>  Se si raccolgono dati di memoria .NET \(allocazioni e\/o durate degli oggetti\) utilizzando il metodo di campionamento, tutti gli eventi di campionamento specificati dall'utente vengono ignorati e vengono utilizzati le allocazioni di memoria e\/o gli eventi di Garbage Collection appropriati per raccogliere dati.  
  
### Per selezionare un evento di esempio  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
2.  In **Pagine delle proprietà** scegliere le proprietà della scheda **Campionamento**.  
  
3.  Dall'elenco a discesa **Evento di campionamento** selezionare l'evento di esempio da utilizzare per profilare un'applicazione.  
  
    > [!NOTE]
    >  L'opzione **Contatori di prestazioni disponibili** è attivata solo se dall'elenco a discesa **Evento di esempio** si sceglie **Contatore di prestazioni**.  
  
4.  Se si seleziona **Contatore di prestazioni**, selezionare un contatore CPU specifico dal controllo di visualizzazione ad albero **Contatori di prestazioni disponibili**.  
  
    -   I contatori inclusi nel nodo **Eventi portabili** sono disponibili in tutti i tipi di processori.  
  
    -   I contatori inclusi nel nodo **Eventi piattaforma** sono specifici del processore del computer corrente e potrebbero non essere disponibili in altri tipi di processori.  
  
5.  Quando si seleziona un evento di esempio, nella casella di testo **Intervallo di campionamento**  viene visualizzato un valore predefinito per l'intervallo di campionamento.  Se necessario, è possibile immettere il valore desiderato nella casella di testo.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)   
 [Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)