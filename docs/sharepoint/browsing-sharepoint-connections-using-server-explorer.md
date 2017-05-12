---
title: "Esplorazione di connessioni di SharePoint tramite Esplora server"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SharePointExplorer.SharePointConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Connessioni di SharePoint [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, esplorazione di siti SharePoint"
  - "sviluppo per SharePoint in Visual Studio, Connessioni di SharePoint"
ms.assetid: b3b1d97b-e990-414c-8ba5-3fd1b463fbef
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Esplorazione di connessioni di SharePoint tramite Esplora server
  È ora possibile esplorare le connessioni locali di SharePoint in **Esplora server**.  Utilizzando questa tecnica, è possibile navigare attraverso i componenti di un sito SharePoint nel sistema.  I componenti dei siti di SharePoint, come ad esempio la definizioni di elenco e i tipi di contenuto, vengono visualizzati in un nodo denominato **Connessioni di SharePoint** nella struttura ad albero della finestra **Esplora server**.  Per visualizzare **Esplora server**, nella barra dei menu, scegliere **Visualizza**, **Esplora server**.  Oltre a visualizzare i componenti del sito di SharePoint, è possibile rimuovere gli elementi, visualizzare le proprietà o aggiornare la visualizzazione della struttura ad albero utilizzando i comandi del menu di scelta rapida.  
  
> [!IMPORTANT]  
>  Per esplorare un sito di SharePoint, è necessario essere amministratore della raccolta siti di SharePoint ed eseguire Visual Studio come un utente amministratore locale del sistema.  In caso contrario, il sito verrà visualizzato in **Esplora server**, ma non sarà possibile espanderne il nodo.  Per verificare se un utente è amministratore della raccolta siti, aprire il sito in un browser, aprire il menu **Azioni sito**, scegliere **Autorizzazioni sito** quindi, nella pagina **Permessi: Sito team**, scegliere il comando **Amministratori raccolta siti** dal gruppo **Gestisci** sulla barra multifunzione.  Se si è un amministratore della raccolta siti, nella casella di testo verrà visualizzato il nome.  Se il comando **Amministratori raccolta siti** non viene visualizzato nel gruppo di gestione nella barra multifunzione, non si dispone dei privilegi di amministratore della raccolta siti, ed è necessario ottenere le autorizzazioni appropriate dall'amministratore del sito.  
  
## Nodi di Esplora server  
 Ogni componente di un sito di SharePoint è rappresentato nella visualizzazione struttura ad albero **Esplora server** da un nodo sotto **Connessioni di SharePoint**.  Ad esempio nei siti di SharePoint predefiniti è disponibile un tipo di contenuto definito Discussione che rappresenta un tipo di discussione visualizzato nella pagina **Discussioni** del sito di SharePoint.  Nel tipo di contenuto Discussione sono presenti diversi campi.  Per visualizzare questi campi in **SharePoint Explorer** espandere il nodo **Tipi contenuto** e successivamente il nodo **Discussione**.  Sotto quest'ultimo sono presenti diversi nodi dei campi, ad esempio Corpo, Oggetto della discussione e Titolo.  
  
## Comandi del menu di scelta rapida dei nodi  
 Ogni nodo dispone di un menu di scelta rapida che può essere acceduto mediante un clic sul nodo con il pulsante destro del mouse, oppure scegliendolo e premendo la combinazione di tasti MAIUSC\+F10.  Di seguito sono riportati alcuni comandi dei nodi:  
  
|Nome comando|Descrizione|  
|------------------|-----------------|  
|Aggiorna|Consente di aggiornare la visualizzazione struttura ad albero affinché venga resa effettiva qualsiasi modifica apportata dall'ultima visualizzazione del nodo.|  
|Delete|Consente di rimuovere il nodo selezionato dalla visualizzazione struttura ad albero. **Note:**  Tale comando è abilitato solo per le connessioni di SharePoint elencate sotto il nodo **Connessioni di SharePoint**.|  
|Proprietà|Consente di visualizzare le proprietà disponibili per il nodo selezionato nella finestra **Proprietà**.  Le proprietà sono tutte di sola lettura e non tutti i nodi dispongono di proprietà associate.|  
|Aggiungi connessione|Consente di specificare un sito di SharePoint che si desidera esplorare.  Disponibile nel nodo **Connessioni di SharePoint** e nei nodi dei siti secondari.|  
|Visualizza nel browser|L'elenco selezionato viene visualizzato nel browser.  Questo comando è disponibile in alcuni elenchi in corrispondenza del nodo **Elenchi** contenuto in **Elenchi e raccolte**.|  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura: aggiungere o rimuovere connessioni di SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Vengono descritti i passaggi richiesti per l'aggiunta di un nuovo sito di SharePoint al nodo **Connessioni di SharePoint** in **Esplora server**.|  
  
## Vedere anche  
 [Server Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  