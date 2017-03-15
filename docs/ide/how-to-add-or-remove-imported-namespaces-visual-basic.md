---
title: "Procedura: aggiungere o rimuovere spazi dei nomi importati (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggiunta di spazi dei nomi importati"
  - "spazi dei nomi importati [Visual Studio]"
  - "spazi dei nomi [Visual Studio], importati"
  - "riferimenti [Visual Studio], spazi dei nomi importati"
  - "rimozione di spazi dei nomi importati"
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedura: aggiungere o rimuovere spazi dei nomi importati (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'importazione di uno spazio dei nomi consente di utilizzare nel codice elementi tratti da tale spazio senza doverli qualificare in modo completo.  Se, ad esempio, si desidera accedere al metodo `Create` nella classe `System.Messaging.MessageQueue`, è possibile importare lo spazio dei nomi `System.Messaging` e fare riferimento solo all'elemento richiesto nel codice come `MessageQueue.Create`.  
  
 Gli spazi dei nomi importati vengono gestiti nella pagina **Riferimenti** di **Progettazione progetti**.  Le importazioni specificate in questa finestra di dialogo vengono passate direttamente al compilatore \(`/imports`\) e utilizzate per tutti i file del progetto.  L'istruzione `Imports` consente di utilizzare uno spazio dei nomi in singoli file del codice sorgente.  
  
### Per aggiungere uno spazio dei nomi importato  
  
1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  
  
2.  Fare clic sulla scheda **Riferimenti** in **Progettazione progetti**.  
  
3.  Nell'elenco **Spazi dei nomi importati**, selezionare la casella di controllo per lo spazio dei nomi da aggiungere.  
  
    > [!NOTE]
    >  Per essere importato, lo spazio dei nomi deve trovarsi in un componente di riferimento.  Se lo spazio dei nomi non è incluso nell'elenco, è necessario aggiungere un riferimento al componente che lo contiene.  Per ulteriori informazioni, vedere [Procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/it-it/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
### Per rimuovere uno spazio dei nomi importato  
  
1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  
  
2.  Fare clic sulla scheda **Riferimenti** in **Progettazione progetti**.  
  
3.  Nell'elenco **Spazi dei nomi importati**, deselezionare la casella di controllo per lo spazio dei nomi da rimuovere.  
  
## Importazione utente  
 Le importazioni utente consentono di importare una classe specifica all'interno di uno spazio dei nomi anziché l'intero spazio dei nomi.  Ad esempio, è possibile che un'applicazione esegua l'importazione di uno spazio dei nomi `Systems.Diagnostics` ma che l'unica classe all'interno dello spazio dei nomi a cui l'utente sia interessato sia `Debug`.  È possibile specificare `System.Diagnostics.Debug` come importazione utente, quindi rimuovere l'importazione per `System.Diagnostics`.  
  
 Se in seguito si decide di importare la classe `EventLog`, è possibile specificare `System.Diagnostics.EventLog` come importazione utente e sovrascrivere`System.Diagnostics.Debug` utilizzando la funzione di aggiornamento.  
  
#### Per aggiungere un'importazione utente  
  
1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  
  
2.  Fare clic sulla scheda **Riferimenti** in **Progettazione progetti**.  
  
3.  Nella casella di testo sotto l'elenco **Spazi dei nomi importati** immettere il nome completo dello spazio dei nomi da importare, incluso lo spazio dei nomi di primo livello.  
  
4.  Fare clic sul pulsante **Aggiungi importazione utente** per aggiungere lo spazio dei nomi all'elenco **Spazi dei nomi importati**.  
  
    > [!NOTE]
    >  Il pulsante **Aggiungi importazione utente** è disabilitato se lo spazio dei nomi corrisponde a uno spazio dei nomi già incluso nell'elenco. Non è possibile infatti aggiungere due volte la stessa importazione.  
  
#### Per aggiornare un'importazione utente  
  
1.  In **Esplora soluzioni** fare doppio clic sul nodo **Progetto** del progetto.  
  
2.  Fare clic sulla scheda **Riferimenti** in **Progettazione progetti**.  
  
3.  Nell'elenco **Spazi dei nomi importati** selezionare lo spazio dei nomi da modificare.  
  
4.  Nella casella di testo sotto l'elenco **Spazi dei nomi importati** immettere il nome del nuovo spazio dei nomi.  
  
5.  Fare clic sul pulsante **Aggiorna importazione utente** per aggiornare lo spazio dei nomi nell'elenco **Spazio dei nomi importati**.  
  
## Vedere anche  
 [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)