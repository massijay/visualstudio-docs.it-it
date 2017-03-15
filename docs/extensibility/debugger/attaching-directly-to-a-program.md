---
title: "La connessione direttamente a un programma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, connessione a programmi"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# La connessione direttamente a un programma
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli utenti che desiderano ai programmi di debug in un processo già in esecuzione utilizza in genere questo processo:  
  
1.  Nell'IDE, scegliere il comando di **Eseguire il debug di processi** dal menu di **strumenti** .  
  
     Verrà visualizzata la finestra di dialogo **Processi**.  
  
2.  Scegliere un processo e fare clic sul pulsante di **Connessione** .  
  
     La finestra di dialogo di **Connettersi da elaborare** viene visualizzato, specificando tutti i motori \(DEs\) di debug installati nel computer.  
  
3.  Specificare DES da utilizzare per eseguire il debug del processo quindi fare clic su **OK**.  
  
 Il pacchetto di debug consente di avviare una sessione di debug e passa l'elenco di DES.  La sessione di debug a sua volta passa tale elenco, con una funzione di callback, il processo selezionato e chiede quindi al processo per enumerare i programmi in esecuzione.  
  
 A livello di codice, in risposta alla richiesta di un utente, il pacchetto di debug creare un'istanza l'amministratore \(SDM\) di debug della sessione e passa l'elenco di DES selezionato.  Con l'elenco, il pacchetto di debug passa a SDM un'interfaccia di [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) .  Il pacchetto di debug passa l'elenco di DES al processo selezionato chiamando [IDebugProcess2:: Connessione](../../extensibility/debugger/reference/idebugprocess2-attach.md).  Lo SDM chiama quindi [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) sulla porta per enumerare i programmi in esecuzione nel processo.  
  
 A partire dall'elenco, ogni modulo di debug è associato a un programma esattamente come illustrato in dettaglio in [Connessione all'avvio](../../extensibility/debugger/attaching-after-a-launch.md), con due eccezioni.  
  
 Per maggiore efficienza, DES distribuiti per condividere uno spazio degli indirizzi con lo SDM gli viene raggruppato in modo che ogni DE disponga di un set di programmi verranno aggiunti a.  In questo caso, chiamate [IDebugEngine2:: Connessione](../../extensibility/debugger/reference/idebugengine2-attach.md) di [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) e passa una matrice di programmi da connettere.  
  
 La seconda eccezione è che gli eventi di avvio inviati da un DE che si connette a un programma già in esecuzione in genere non includono l'evento del punto di ingresso.  
  
## Vedere anche  
 [L'invio di eventi di avvio dopo il lancio di un](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)