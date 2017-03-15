---
title: "Scheda Generale, finestra di dialogo Propriet&#224; thread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [Visual Studio], proprietà thread"
  - "proprietà thread"
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Scheda Generale, finestra di dialogo Propriet&#224; thread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzare questa finestra di dialogo per ottenere ulteriori informazioni su un thread specifico.  Per visualizzare questa finestra di dialogo, spostare lo stato attivo su una finestra [Visualizzazione thread](../debugger/threads-view.md) o aprire [Visualizzazione messaggi](../debugger/messages-view.md) ed espandere un messaggio.  Selezionare un nodo qualsiasi del thread nella struttura ad albero, quindi scegliere **Proprietà** dal menu **Visualizza**.  
  
 Nella finestra di dialogo **Proprietà thread** è incluso un solo riquadro, ossia la scheda **Generale**.  Sono disponibili le impostazioni seguenti:  
  
|Voce|Descrizione|  
|----------|-----------------|  
|**Module Name**|Nome del modulo.|  
|**ID thread**|ID univoco di questo thread.  Si noti che i numeri di ID del thread vengono riutilizzati e pertanto identificano un thread solo per la relativa durata.|  
|**ID processo**|ID univoco di questo processo.  I numeri di ID del processo vengono riutilizzati e pertanto identificano un processo solo per la relativa durata.  Il tipo di oggetto Process viene creato durante l'esecuzione di un programma.  Tutti i thread in un processo condividono lo stesso spazio degli indirizzi e hanno accesso agli stessi dati.  Scegliere questo valore per visualizzare le proprietà dell'ID processo.|  
|**Thread State**|Stato corrente del thread.  Un thread in esecuzione sta utilizzando un processore, mentre un thread in standby sta per utilizzarne uno.  Un thread pronto è in attesa di utilizzare un processore perché non è disponibile.  Un thread in transizione è in attesa dell'esecuzione di una risorsa, ad esempio che venga eseguito il paging da disco dello stack di esecuzione.  Un thread in attesa non richiede il processore perché sta attendendo che un'operazione periferica venga completata o che una risorsa diventi disponibile.|  
|**Wait Reason**|Applicabile solo quando il thread è nello stato di attesa.  Vengono utilizzate coppie di eventi per comunicare con i sottosistemi protetti.|  
|**CPU Time**|Tempo CPU totale trascorso su questo processo e i relativi thread.  Corrisponde a User Time \+ Privileged Time.|  
|**User Time**|Tempo totale trascorso impiegato dal thread per l'esecuzione di codice in modalità utente.  Le applicazioni vengono eseguite in modalità utente, analogamente a sottosistemi quali la gestione finestre e il motore della grafica.|  
|**Privileged Time**|Tempo totale trascorso impiegato dal thread per l'esecuzione di codice in modalità privilegiata.  Quando viene chiamato, un servizio di sistema di Windows viene spesso eseguito in modalità privilegiata per poter accedere a dati privati del sistema.  Tali dati sono protetti dall'accesso da parte di thread in esecuzione in modalità utente.  Le chiamate al sistema possono essere esplicite o implicite, come quando si verifica un errore di pagina o un'interruzione.|  
|**Tempo trascorso**|Il tempo totale \(in secondi\) trascorso da quando il thread è in esecuzione.|  
|**Current Priority**|Priorità dinamica corrente del thread.  La priorità di base dei thread all'interno di un processo può aumentare o diminuire in relazione alla priorità di base del processo.|  
|**Base Priority**|Priorità di base corrente del thread.|  
|**Start Address**|Indirizzo virtuale iniziale per il thread.|  
|**User PC**|Contatore del programma utente per il thread.|  
|**Context Switches**|Numero di passaggi da un thread a un altro.  Tali passaggi possono avvenire all'interno di un singolo processo o tra processi  e possono essere causati da una richiesta di informazioni tra thread o dal superamento di un thread da parte di un altro con priorità più elevata pronto all'esecuzione.|