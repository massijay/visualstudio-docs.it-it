---
title: "Descrizioni degli eventi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], eventi"
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Descrizioni degli eventi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ogni tipo di evento ha uno scopo specifico.  
  
## Eventi e i motivi per il loro utilizzo  
  
|Evento|Descrizione|  
|------------|-----------------|  
|Attivare eventi del documento|Verificare quando il motore di \(DE\) debug desidera l'ide per aprire o aggiornare un documento in primo piano.|  
|Limite del punto di interruzione o eventi di errore del punto di interruzione|Inviato quando un punto di interruzione verrà associato o quando un punto di interruzione non può essere associato e viene restituito un errore.|  
|Eventi non associati del punto di interruzione|Verificare quando un punto di interruzione associato separa il codice.|  
|Consente di arrestare gli eventi|Inviato all'IDE per determinare se l'utente richieste interruzione in un punto specificato nel codice.|  
|Eventi del punto di interruzione|Verificare quando un punto di interruzione dei dati o di codice viene premuto.|  
|Eventi del testo del documento|Verificare quando il testo in un documento viene modificato.  Questi eventi non vengono inviati con il metodo di `IDebugEventCallBack2::Event` .|  
|il motore crea gli eventi|Inviato quando un modulo viene inizialmente creato.|  
|Eventi del punto di ingresso|Inviato quando il programma sottoposto a debug ha eseguito il codice di inizializzazione e ha raggiunto il primo punto di ingresso dell'utente.|  
|eventi di eccezione|Inviato quando un programma in esecuzione premere un'eccezione.|  
|Eventi completi di valutazione di espressioni|Inviato durante la valutazione asincrona di espressione è completa.|  
|Eventi del simbolo di ricerca|Inviato ogni volta che il DE necessario chiedere all'utente di individuare i simboli per un modulo.|  
|Eventi completamento del caricamento|Inviato solo quando il caricamento del programma iniziale è completo e il primo codice sta peresecuzione del programma.|  
|Eventi di messaggio|Inviato quando i messaggi vengono inviati agli utenti.|  
|Eventi di caricamento dei moduli|Inviato quando un nuovo modulo viene caricato o scaricato.|  
|Eventi di output della stringa|inviato quando il programma scrive l'output di debug.|  
|Creare ed eliminare gli eventi|Inviato per annunciare la creazione o la distruzione dei processi, programmi, proprietà, sessioni e thread pertanto IDE di Visual Studio può tenere traccia dello stato dei programmi in corso il debug.|  
|Eventi completi di passaggio|inviato quando un passaggio è completo.|  
|Eventi di cambio del nome del thread|inviato quando l'utente modifica il nome di un thread.|  
|Eventi di modifica del nome del programma|inviato quando l'utente modifica il nome di un programma.|  
  
## Vedere anche  
 [L'invio di eventi](../../extensibility/debugger/sending-events.md)