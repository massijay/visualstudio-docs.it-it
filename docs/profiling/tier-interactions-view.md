---
title: "Visualizzazione Interazioni tra livelli | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "Interazioni tra livelli (visualizzazione)"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Interazioni tra livelli
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La profilatura interazione tra livelli offre informazioni aggiuntive sui tempi di esecuzione nelle funzioni in applicazioni multilivello che comunicano con database tramite [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)].  I dati vengono raccolti solo per chiamate di funzione sincrone.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 Nella visualizzazione delle interazioni i dati di interazione dei livelli vengono visualizzati in due riquadri:  
  
-   Il riquadro master è una struttura ad albero gerarchica.  La riga di primo livello contiene i dati aggregati relativi alle connessioni di database di una pagina [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o di un processo.  I nodi figlio contengono i dati aggregati delle connessioni di database del padre.  
  
-   Quando si fa clic su un nodo delle chiamate al database nel riquadro master, vengono visualizzati i dati per l'istanza della chiamata al database nel riquadro dei dettagli.  
  
 Il tempo viene visualizzato come il numero di millisecondi o come il numero di cicli macchina CPU.  Per modificare l'unità di tempo visualizzata, fare clic sul menu **Strumenti**, su **Opzioni**, quindi scegliere una delle opzioni **Mostra i valori di durata in**.  
  
## Riquadro master  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|-   Per una riga di primo livello, nome del processo o della pagina Web profilata.<br />-   Per una riga di connessione al database, nome del server che ospita il database.|  
|**Database**|Nome del database \(solo righe di connessione al database\).|  
|**Conteggio**|Numero totale di richieste generate dal processo, dalla pagina Web o dalla connessione al database.|  
|**Tempo trascorso totale**|Quantità totale di tempo trascorso durante l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione al database.|  
|**Tempo trascorso massimo**|Quantità massima di tempo trascorso durante l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione al database.|  
|**Tempo trascorso minimo**|Quantità minima di tempo trascorso durante l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione al database.|  
|**Tempo trascorso medio**|Tempo medio trascorso durante l'esecuzione di una richiesta dal processo, dalla pagina Web o dalla connessione al database.|  
  
## Riquadro Dettagli connessione database  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Testo del comando**|Query SQL della richiesta.|  
|**Conteggio query**|Numero di volte in cui è stata eseguita la query.|  
|**Tempo trascorso totale**|Tempo totale trascorso durante l'esecuzione delle istanze della query.|  
|**Tempo trascorso massimo**|Quantità massima di tempo trascorso durante l'esecuzione di un'istanza della query.|  
|**Tempo trascorso minimo**|Quantità minima di tempo trascorso durante l'esecuzione di un'istanza della query.|  
|**Tempo trascorso medio**|Tempo medio trascorso durante l'esecuzione di un'istanza della query.|