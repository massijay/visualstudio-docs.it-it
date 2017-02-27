---
title: "Applicazione delle impostazioni tra pi&#249; connessioni di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, applicazione di impostazioni"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Applicazione delle impostazioni tra pi&#249; connessioni di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un plug\-in controllo del codice sorgente compilato utilizzando il plug\-in controllo del codice sorgente l'API 1,2, può utilizzare un'operazione di blocco per eseguire la stessa operazione di controllo del codice sorgente in più progetti o i contesti di connessione con.  I batch possono essere utilizzati per eliminare ridondante, finestre di dialogo di VC\+\+ dall'esperienza utente.  
  
 Se un utente seleziona più elementi appartenenti a più di una connessione in un plug\-in controllo del codice sorgente compilato utilizzando il plug\-in controllo del codice sorgente l'API 1,1, ad esempio, due progetti Web in computer diversi di condivisione di file\) e li l'estrazione, riceverà più volte la stessa finestra di dialogo.  Questo accade anche se l'utente seleziona la casella di controllo di **Applicare a tutti** nella finestra di dialogo, perché l'ide reimposta il relativo stato per ogni contesto di connessione.  
  
## Nuovo contrassegno di funzionalità  
 la funzione di`SccBeginBatch` imposta il flag di `SCC_CAP_BATCH` per indicare che un'operazione di blocco è in corso  
  
## nuove funzioni  
 Le nuove funzioni seguenti supportano l'operazione di blocco:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 La funzione di `SCCBeginBatch` avvia un gruppo di operazioni di controllo del codice sorgente.  `SccEndBatch` chiude il gruppo.  i gruppi non possono essere annidati.  
  
## Vedere anche  
 [Novità di origine controllo plug\-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)