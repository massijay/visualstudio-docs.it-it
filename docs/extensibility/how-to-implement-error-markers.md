---
title: "Procedura: implementare i marcatori di errore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - marcatori di errore"
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedura: implementare i marcatori di errore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I marcatori di errori o ondulate rosse\) sono i più difficile delle personalizzazioni dell'editor di testo da distribuire.  Tuttavia, i vantaggi che forniscono agli utenti del package VS possono per superare il costo di pesatura per consentire loro.  I marcatori di errore indicano sottile il testo che il parser dà errato con una linea ondulata rossa o ondulata.  Questo indicatore consente ai programmatori visivamente visualizzare codice non corretto.  
  
 Marcatori di testo di utilizzo per implementare le linee ondulate.  In generale, i servizi di linguaggio aggiunti le linee ondulate al buffer di testo come sessione in background, in fase di inattività o in un thread in background.  
  
### Per implementare la funzionalità rossa la linea ondulata  
  
1.  Selezionare il testo che si intende utilizzare il posto la linea ondulata rossa.  
  
2.  Creare un marcatore del tipo `MARKER_CODESENSE_ERROR`.  Per ulteriori informazioni, vedere [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md).  
  
3.  Successivamente, passare un puntatore a interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
 Questo processo consente anche di creare il testo del suggerimento o un menu di scelta rapida speciale su un marcatore specificato.  Per ulteriori informazioni, vedere [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md).  
  
 Gli oggetti sono necessari prima che i marcatori di errori possano essere visualizzati.  
  
-   un parser.  
  
-   Un provider dell'attività \(ovvero un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\) che gestisce un record delle modifiche delle informazioni sulla riga per identificare le linee ri\-da analizzare.  
  
-   Un filtro di visualizzazione di testo che acquisisce gli eventi di modifica del cursore dalla visualizzazione utilizzando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>\).  
  
 Il parser, il provider di attività e il filtro fornisce l'infrastruttura necessaria per consentire i marcatori di errori.  I passaggi seguenti forniscono il processo per visualizzare marcatori di errori.  
  
1.  In una visualizzazione che sta filtrare, il filtro ottiene un puntatore al provider di attività associato ai dati della visualizzazione.  
  
    > [!NOTE]
    >  È possibile utilizzare lo stesso filtro per i suggerimenti di metodo, il completamento delle istruzioni, i marcatori dal comando di errori, e così via.  
  
2.  Quando il filtro riceve un evento che indica che è stato spostato in un'altra riga, viene creata un'attività per verificare la presenza di errori.  
  
3.  I controlli del gestore di attività se la riga è stata modificata.  In caso affermativo, analizza la riga per gli errori.  
  
4.  Se gli errori vengono trovati, il provider di attività crea un'istanza dell'attività.  Questa istanza viene creato il marcatore di testo che l'ambiente utilizza come marcatore di errori nella visualizzazione di testo.  
  
## Vedere anche  
 [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)   
 [Procedura: creare indicatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)   
 [Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)