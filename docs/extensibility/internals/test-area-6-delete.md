---
title: "Test Area 6: eliminare | Microsoft Docs"
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
  - "controllo del codice sorgente [Visual Studio SDK], eliminazione elementi"
  - "origine plug-in del controllo, l'eliminazione di elementi"
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Test Area 6: eliminare
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quest'area esempio di plug\-in controllo del codice sorgente relative alle azioni di eliminazione.  
  
 Il controllo del codice sorgente rispondono alle azioni di eliminazione in **Esplora soluzioni**.  
  
 Segue un elenco di elementi che possono essere eliminati:  
  
-   File  
  
-   Cartelle  
  
-   Project  
  
 A seconda dello scenario, l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> viene generato dopo i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>.  Qualsiasi azione eliminerà il progetto o elemento da **Esplora soluzioni**.  
  
## comportamento previsto  
 Il comportamento previsto per i test case nell'esempio di eliminazione è:  
  
-   L'elemento eliminati non è più visibile all'interno di **Esplora soluzioni**.  
  
-   Il padre del progetto dell'elemento o eliminato è verificato in base alle esigenze \(possibilmente con una richiesta.\)  
  
-   Dopo avere eliminato verificato o l'elemento aggiunto, non viene visualizzato nella finestra di **In attesa dei controlli** .  
  
-   L'elemento è ancora presente all'interno dell'archivio di controllo del codice sorgente, anche dopo l'eliminazione e manualmente essere purgato.  
  
|Azione|Passi del test|I risultati previsti da verificarsi|  
|------------|--------------------|-----------------------------------------|  
|eliminare un progetto client|1.  creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Rimuovere l'intero progetto da una soluzione|Comportamento previsto di uso comune.|  
|eliminare un file vuoto|1.  creare un progetto client.<br />2.  Aggiungere un file a zero byte al progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  selezionare il file, eliminarlo.|Comportamento previsto di uso comune.|  
|Per eliminare una cartella con un file|1.  Creare la soluzione del progetto.<br />2.  aggiungere una cartella.<br />3.  Aggiungere un file alla cartella.<br />4.  Aggiungere la soluzione al controllo del codice sorgente.<br />5.  Estrarre il progetto per evitare le richieste.<br />6.  eliminare la cartella.|Comportamento previsto di uso comune.|  
|Eliminare un progetto Web di file system|1.  Creare un progetto Web di file system \(utilizzare il pulsante sfoglia per specificare un percorso UNC\).<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Rimuovere l'intero progetto dalla soluzione.<br />4.  Ripetere i passaggi da 1 a 3 per un progetto Web locale \(percorsi diversi di da uno con il codice ma ha la stessa interfaccia esterna e comportamento\).|Comportamento previsto di uso comune.|  
|Eliminare un file da un progetto Web di file system|1.  Creare un progetto Web di file system.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Eliminare un file dal progetto.<br />4.  Ripetere i passaggi da 1 a 3 per un progetto Web locale \(percorsi diversi di da uno con il codice ma ha la stessa interfaccia esterna e comportamento\).|Comportamento previsto di uso comune.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)