---
title: "Procedura: eseguire il debug con codice sorgente di Code Center Premium | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Code Center Premium"
  - "debug [Visual Studio], Code Center Premium"
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: eseguire il debug con codice sorgente di Code Center Premium
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con il debugger di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] è possibile eseguire il debug di codice sorgente condiviso sicuro disponibile in Microsoft MSDN Code Center Premium.  
  
 In questo argomento viene descritto come impostare Code Center Premium e come eseguire il debug del relativo codice sorgente in Visual Studio.  
  
### Per prepararsi all'esecuzione del debug con Code Center Premium  
  
1.  Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2.  Avviare Visual Studio.  
  
3.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
4.  Nella finestra di dialogo **Opzioni** aprire il nodo **Debug** e scegliere **Generale**.  
  
5.  Deselezionare la casella di controllo **Abilita Just My Code \(solo gestito\)**.  
  
6.  Selezionare **Abilita il supporto del server di origine**.  
  
7.  Deselezionare **Richiedi corrispondenza esatta dei file di origine con la versione originale**.  
  
8.  Nel nodo **Debug** selezionare **Simboli**.  
  
9. Nella casella **Percorsi dei file di simboli \(pdb\)** deselezionare la casella di controllo **Server dei simboli Microsoft** e aggiungere i percorsi seguenti:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Accertarsi di includere la barra finale**\/** alla fine del percorso.  
  
     Spostare questi percorsi all'inizio dell'elenco per assicurarsi che questi simboli vengano caricati per primi.  
  
    > [!NOTE]
    >  Questi percorsi di Code Center Premium devono essere elencati per primi in modo che vengano caricati per primi.  In Visual Studio 2010, non è possibile spostare server sopra la voce **Server dei simboli Microsoft**, ecco perché è necessario deselezionare la casella di controllo.  
    >   
    >  Per caricare simboli dai simboli Microsoft durante la sessione di debug, eseguire questa operazione:  
    >   
    >  1.  Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Moduli**.  
    > 2.  Selezionare il modulo di cui si desidera caricare simboli, quindi aprire il menu di scelta rapida.  Scegliere **Carica simboli da**, quindi scegliere **Server dei simboli Microsoft**.  
  
10. Nella casella **Memorizza nella cache i simboli dai server di simboli in questa directory** immettere un percorso, ad esempio `C:\symbols`, in cui Code Center Premium può memorizzare nella cache i simboli.  La memorizzazione nella cache dei simboli può contribuire a migliorare le prestazioni durante il debug.  
  
     Se si verificano dei problemi durante il debug del codice sorgente con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dopo avere completato questa procedura, controllare il percorso della cache per i file di simboli non aggiornati e memorizzati nella cache.  Rimuovere i file di simboli non aggiornati.  
  
11. Scegliere **OK**.  
  
12. Riavviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per assicurarsi che le impostazioni siano state salvate in modo permanente.  
  
### Per eseguire il debug del codice sorgente utilizzando Connetti a processo  
  
1.  Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2.  Avviare Visual Studio.  
  
3.  Aprire il progetto di Visual Studio.  
  
4.  Scegliere **Connetti a processo** dal menu **Strumenti**.  
  
5.  Nella finestra di dialogo **Connetti a processo** scegliere **Seleziona**.  
  
6.  Nella finestra di dialogo **Seleziona tipo di codice**, in **Rileva questi tipi di codice**, selezionare **Nativo**, **Gestito** e **Gestito\(v4.0\)**.  
  
7.  Scegliere **OK** per chiudere la finestra di dialogo **Seleziona tipo di codice**.  
  
8.  Nella casella **Processi disponibili** selezionare il processo di cui si desidera eseguire il debug.  
  
9. Scegliere **Connetti**.  
  
10. Quando viene richiesto di confermare il certificato, fare clic su **OK**.  Immettere il PIN.  Se richiesto, accettare le condizioni per l'utilizzo di Code Center Premium.  
  
     Il download dei simboli può richiedere molto tempo, a seconda della velocità della rete.  Sulla barra di stato verrà indicato quando tutti i simboli sono stati scaricati correttamente.  
  
11. Ripetere i passaggi di connessione per tutti i progetti gestiti nella soluzione.  
  
### Per eseguire il debug del codice sorgente da una soluzione esistente  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per la soluzione, quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo Pagine delle proprietà della soluzione scegliere **Esegui debug dei file di origine** nel nodo **Proprietà comuni**.  
  
3.  Aggiungere il percorso seguente nell'elenco **Directory che contengono file di origine**:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Accertarsi di includere la barra finale**\/** alla fine del percorso.  
  
4.  Per ogni progetto gestito nella soluzione, eseguire quanto segue:  
  
    1.  In Esplora soluzioni aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
    2.  Selezionare **Debug** e scegliere **Attiva debug codice non gestito**.  
  
### Per eseguire il debug della soluzione con l'origine Code Center Premium  
  
1.  Nella classe `Package` impostare un punto di interruzione nel costruttore del pacchetto.  
  
2.  Scegliere **Avvia debug** dal menu `Debug`.  
  
3.  Quando si raggiunge il punto di interruzione nel costruttore del pacchetto, accedere alla finestra **Stack di chiamate** e fare clic con il pulsante destro del mouse sullo stack frame dell'assembly da cui si desidera caricare i simboli, quindi fare clic su **Carica simboli**.  
  
     Fare doppio clic sul frame di chiamata per caricare l'origine.  
  
### Per analizzare il codice sorgente in Code Center Premium  
  
1.  Collegare il lettore SmartCard e inserire la scheda ottenuta dall'iniziativa Shared Source.  
  
2.  Avviare Internet Explorer e immettere l'URL `https://codepremium.msdn.microsoft.com`  
  
3.  Cercare il codice sorgente desiderato.  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)