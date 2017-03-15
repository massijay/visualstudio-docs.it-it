---
title: "Test Area 8: Cambio del plug- | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], cambio plug-in"
  - "origine plug-in del controllo, cambio"
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Test Area 8: Cambio del plug-
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'ambiente di sviluppo integrato di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(IDE\)interfaccia utente \(UI\) per la modifica del plug\-in controllo del codice sorgente corrente.  Quest'area esempio fornisce i test case per il processo di raccolto che i plug\-in da utilizzare per il controllo del codice sorgente della soluzione.  
  
## Menu Access di comando  
 I seguenti percorsi del menu dell'ambiente di sviluppo integrato di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati nei test case.  
  
-   Plug\-in controllo del codice sorgente corrente: **strumenti** \- \> **opzioni** \- \> **Controllo del codice sorgente** \- \> **selezione plug\-in**.  
  
-   Associazione del controllo del codice sorgente di modifica: **file** \- \> **Controllo del codice sorgente** \- \> **Controllo del codice sorgente di modifica**…  
  
## Comportamento previsto comuni  
 Modificare il plug\-in controllo del codice sorgente di una soluzione è possibile senza uscire da Visual Studio o ricaricare la soluzione.  Inoltre, cambia di plug\-in controllo del codice sorgente automaticamente a quella che hanno utilizzato da una soluzione quando la soluzione viene caricata.  
  
## Test case  
 Di seguito sono illustrati i test case specifici per l'area di plug\-in di commutazione.  
  
### caso 8a: modifica automatica  
  
#### comportamento previsto  
 Quando un utente carica una soluzione inclusa nel controllo del codice sorgente, la soluzione viene caricato automaticamente e il plug\-in controllo del codice sorgente appropriato viene selezionato come corrente.  
  
|Azione|Passi del test|I risultati previsti da verificarsi|  
|------------|--------------------|-----------------------------------------|  
|Modifica automatica di plug\-in controllo del codice sorgente|1.  Plug\-in selezionato sotto test come corrente \(**strumenti** \- \> **opzioni** \- \> **Controllo del codice sorgente** \- \> **selezione plug\-in**\).<br />2.  Creare un nuovo progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Selezionare un altro plug\-in, ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />5.  Accettare lo scaricamento di richiesta della soluzione.<br />6.  Riaprire la soluzione da disco.|la soluzione è aperta.<br /><br /> Il plug\-in sottoposta a test è il plug\-in controllo del codice sorgente corrente.|  
  
### caso 8b: La modifica basata su soluzione  
  
#### comportamento previsto  
 La soluzione può avere il plug\-in controllo del codice sorgente associato modificato.  
  
|Azione|Passi del test|I risultati previsti da verificarsi|  
|------------|--------------------|-----------------------------------------|  
|Modifica del plug\-in per una soluzione|1.  Plug\-in selezionato sotto test come corrente \(**strumenti** \- \> **opzioni** \- \> **Controllo del codice sorgente** \- \> **selezione plug\-in**\).<br />2.  Creare un nuovo progetto e soluzione.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Separare la soluzione dal controllo del codice sorgente \(utilizzando la finestra di dialogo **Controllo del codice sorgente di modifica** \).<br />5.  Selezionare un altro plug\-in, ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />6.  Ricaricare la soluzione dal disco se scaricato.<br />7.  Aggiungere la soluzione al controllo del codice sorgente.<br />8.  Separare la soluzione dal controllo del codice sorgente \(utilizzando la finestra di dialogo **Modificare il controllo del codice sorgente** \).<br />9. Plug\-in selezionato sottoposta a test.<br />10. Ricaricare la soluzione dal disco se scaricato.<br />11. Associa la soluzione nel percorso originale \(utilizzando la finestra di dialogo **Controllo del codice sorgente di modifica** \).|La soluzione verrà aggiunto al controllo del codice sorgente mediante il plug\-in selezionato.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)