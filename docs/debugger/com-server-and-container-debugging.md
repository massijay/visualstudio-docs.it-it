---
title: "Debug dei server e dei contenitori COM | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "controlli ActiveX (debug del contenitore) [Visual Studio]"
  - "controlli ActiveX, debug"
  - "COM [Visual Studio], debug"
  - "COM (server), debug"
  - "debug dei controlli ActiveX"
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Debug dei server e dei contenitori COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le applicazioni COM eseguono alcune attività che non sono sotto il controllo diretto del programmatore.  Le comunicazioni tra le DLL, il conteggio di utilizzo degli oggetti e le operazioni relative agli Appunti rappresentano solo alcune delle aree nelle quali potrebbero verificarsi comportamenti non prevedibili.  In questi casi il primo passo consiste nel tracciare il codice sorgente.  
  
 Il debugger di Visual Studio supporta l'esecuzione delle istruzioni attraverso i contenitori e i server e all'interno di essi.  Tale supporto include la capacità di eseguire le istruzioni RPC \(Remote Procedure Call, chiamata a procedura remota\).  
  
## In questo argomento  
  
1.  [Debug di un server COM e di un contenitore nella stessa soluzione](../debugger/com-server-and-container-debugging.md#BKMK_COMServerandContainerintheSameSolution)  
  
2.  [Debug di un'applicazione server senza informazioni sul contenitore](../debugger/com-server-and-container-debugging.md#BKMK_ServerApplicationWithoutContainerInformation)  
  
3.  [Debug di un'applicazione di isolamento server e dominio (SDI)](../debugger/com-server-and-container-debugging.md#BKMK_DebuggingaServerandDomainIsolationSDIApplication)  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Debug di un server COM e di un contenitore nella stessa soluzione  
 È possibile eseguire il debug di un server e di un contenitore COM utilizzando due progetti all'interno della stessa soluzione.  Impostare i punti di interruzione appropriati in ogni progetto e procedere al debug.  Quando il contenitore effettua una chiamata nel codice del server in cui è stato impostato un punto di interruzione, il contenitore resta in attesa della fine dell'esecuzione del codice del server ovvero il termine del relativo debug.  
  
 Il debug di un contenitore COM è simile a quello di un programma standard.  Presenta invece delle differenze quando si riferisce a un evento che genera un callback, ad esempio il trascinamento di dati in un'applicazione contenitore.  In questo caso, è necessario impostare un punto di interruzione nella funzione di callback.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debug di un'applicazione server senza informazioni sul contenitore  
 Quando le informazioni di debug relative all'applicazione contenitore non vengono utilizzate o non sono disponibili, l'avvio del debug di un'applicazione server si suddivide in tre passaggi:  
  
1.  Avviare il debug del server come applicazione normale.  
  
2.  Impostare i punti di interruzione nel modo desiderato.  
  
3.  Avviare l'applicazione contenitore.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debug di un'applicazione di isolamento server e dominio \(SDI\)  
 Se si esegue il debug di un'applicazione server SDI, è necessario specificare `/Embedding` o `/Automation` nella proprietà **Argomenti della riga di comando** disponibile nella finestra di dialogo Pagine delle proprietà di *Progetto* per i progetti C\/C\+\+, C\# o Visual Basic.  
  
 Grazie a questi argomenti della riga di comando, il debugger è in grado di avviare l'applicazione server come se tale avvio venisse eseguito da un contenitore.  In seguito all'avvio del contenitore da Program Manager o File Manager, il contenitore utilizzerà l'istanza del server già avviata dal debugger.  
  
 Per accedere alla finestra di dialogo Pagine delle proprietà di *Progetto*, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Proprietà dal menu di scelta rapida.  Per individuare la proprietà Argomenti della riga di comando, espandere la categoria Proprietà di configurazione e fare clic sulla pagina Debug.  
  
## Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)