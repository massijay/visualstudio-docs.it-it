---
title: "Area di test 1: Aggiungere a Apri dal controllo del codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], aggiunta e l'apertura di soluzioni"
  - "origine plug-in del controllo, aggiunta e l'apertura di soluzioni"
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Area di test 1: Aggiungere a / Apri dal controllo del codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questo controllo del codice sorgente del plug\-in di test viene illustrata l'area immissione soluzioni o progetti nel controllo del codice sorgente e il recupero dal controllo del codice sorgente.  
  
## Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi di menu dell'ambiente di sviluppo integrato nei test case:  
  
-   Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], aprire dal controllo del codice sorgente: **File**, **aprire**, **progetto**\/**soluzione**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] percorso.  
  
-   Per altri origine plug\-in del controllo, aprire dal controllo del codice sorgente: **File**, **controllo del codice sorgente**, **aprire dal controllo del codice sorgente**.  
  
-   Aggiungere al controllo del codice sorgente: **File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo codice sorgente**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.  
  
-   Menu di scelta rapida \(progetto\/soluzione\), **Aggiungi soluzione al controllo del codice sorgente**.  
  
-   Aggiungi da controllo del codice sorgente: **File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**.  
  
-   Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], aggiungere dall'origine controllo è disponibile anche in **File**, **Aggiungi**, **progetto esistente**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] percorso.  
  
    > [!NOTE]
    >  In questo test, è possibile utilizzare un percorso di un file locale o un server IIS locale \(server web\).  
  
## Comportamento previsto  
  
-   Per ogni tipo di progetto supportati, un utente deve essere in grado di "Aggiungere" e "Apri" dal controllo del codice sorgente.  
  
-   Quando viene aggiunto un progetto di controllo del codice sorgente corrispondente \<*NomeProgetto*\> viene creato e vspscc file \(file di progetto hint\). Contiene informazioni di connessione e l'elenco di file esclusione. Non eliminare questo file perché contiene informazioni specifiche per il progetto.  
  
-   Quando viene aggiunta una soluzione al controllo del codice sorgente corrispondente \<*SolutionName*\> viene creato il file. vssscc \(triple S\). Il file di testo contiene le informazioni di connessione e un elenco di file di esclusione, simile al file dei suggerimenti di progetto. Questo file è temporaneo ed esiste solo nel database del controllo del codice sorgente.  
  
-   Quando viene aperta una soluzione dal controllo del codice sorgente, un \<*SolutionName*\> file .vsscc \(double S\) che esiste solo nel database di controllo di origine, viene creato in locale in un file temporaneo. Questo file contiene il percorso dalla cartella di connessione della soluzione per il file della soluzione. Questo file è temporaneo e la copia locale viene eliminata quando viene completata l'operazione "Apri dal controllo del codice sorgente".  
  
-   Dopo l'aggiunta di un progetto per il controllo del codice sorgente, è possibile eseguire le azioni di controllo di origine su di esso \(estrazione, Get e così via\).  
  
## Test case  
 Di seguito sono riportati i test case specifici per l'aggiunta di \/ Open dall'area di test di controllo del codice sorgente.  
  
### Caso 1a: Aggiungi soluzione al controllo del codice sorgente  
 Questo test case è incentrato sull'aggiunta di soluzioni al controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Aggiungere una soluzione contenente un progetto client di controllo del codice sorgente|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**\).|Progetto\/soluzione è stata aggiunta al controllo del codice sorgente.|  
|Aggiungere una soluzione contenente un File System o un progetto Web IIS locale al controllo del codice sorgente|1.  Creare un File System o un progetto Web IIS locale \(clic sul pulsante Sfoglia per puntare al percorso del progetto; il percorso determina il tipo di progetto Web viene creato\).<br />2.  Aggiungere la soluzione al controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**\).|Progetto\/soluzione è stata aggiunta al controllo del codice sorgente.|  
|Aggiungere una soluzione contenente un progetto Web del sito remoto al controllo del codice sorgente|1.  Creare un progetto Web del sito remoto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**\).<br />3.  Fare clic su **OK** nella finestra di dialogo Avviso di accesso di FrontPage.|Soluzione è stata aggiunta al controllo del codice sorgente.<br /><br /> Progetto di sito remoto non è incluso nel controllo del codice sorgente. \(I progetti di sito remoto devono essere controllati da un server IIS\).|  
|Aggiungere una singolo progetto soluzione al controllo di origine mediante **Aggiungi progetti selezionati a controllo del codice sorgente**.|1.  Creare una soluzione di singolo progetto.<br />2.  Aggiungere solo soluzione al controllo del codice sorgente come selezione \(**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**\). Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Aggiunta del progetto del controllo del codice sorgente come selezione \(**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**\).<br />4.  Fare clic su **Sì** per aggiungere il progetto nello stesso percorso.<br />5.  Fare clic su **estrazione** in **Estrai per la modifica** la finestra di dialogo.|`Result from Step 2:`<br /><br /> Il progetto e tutti i file all'interno del progetto hanno un all'indicatore di controllo di origine e una descrizione comando visualizzato "non sotto il controllo del codice sorgente".<br /><br /> `Result from Step 5:`<br /><br /> File di progetto e soluzione sono nella stessa cartella nel controllo del codice sorgente.|  
|Annullare l'aggiunta di una soluzione al controllo del codice sorgente|1.  Creare una soluzione di singolo progetto.<br />2.  Tentativo di aggiungere progetti e soluzioni al controllo del codice sorgente. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Annullare una volta nel controllo del codice sorgente.|`Result from Step 2:`<br /><br /> Set progetto percorso origine controllo la finestra di dialogo viene visualizzata una sola volta.<br /><br /> `Result from Step 3:`<br /><br /> Progetto aggiungere annullato, progetto\/soluzione non è incluso nel controllo del codice sorgente e concorrono a menu di controllo di origine ancora disponibili.|  
  
### Case 1b. Aprire la soluzione dal controllo del codice sorgente  
 Questo test case è incentrato sull'apertura di soluzioni dal controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Aprire una soluzione contenente un progetto client dal controllo del codice sorgente|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|Soluzione\/progetto aperto dal controllo del codice sorgente.|  
|Aprire una soluzione contenente un progetto Web IIS da controllo del codice sorgente locale|1.  Creare un progetto Web IIS locale.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|Soluzione\/progetto aperto dal controllo del codice sorgente.|  
|Aprire una soluzione contenente un progetto Web del sito remoto dal controllo del codice sorgente|1.  Creare un progetto Web del sito remoto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|`Result from Step 2:`<br /><br /> Web del sito remoto non è incluso nel controllo del codice sorgente.<br /><br /> `Result from Step 4:`<br /><br /> Soluzione aperta dal controllo del codice sorgente.<br /><br /> Progetto di sito remoto viene caricato, ma non è incluso nel controllo del codice sorgente.|  
  
### Caso 1c: aggiungere soluzioni dal controllo del codice sorgente  
 Questo test case è incentrata sull'aggiunta di soluzioni dal controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Aggiungere alla soluzione vuota, ovvero una singolo progetto soluzione|1.  Creare una soluzione di singolo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare una seconda soluzione vuota.<br />5.  Aggiungere la soluzione in precedenza controllata dal controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**\).|Il progetto aggiunto verrà visualizzato **Esplora** e viene archiviato.|  
|Aggiungere alla soluzione con singolo progetto, ovvero singolo progetto|1.  Creare una soluzione con un singolo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare una seconda soluzione vuota.<br />5.  Aggiungere la soluzione in precedenza controllata dal controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**\).|Il progetto aggiunto verrà visualizzato **Esplora** e viene archiviato.|  
|Aggiungere alla soluzione\-soluzione aggiunto al controllo del codice sorgente in base a selezione|1.  Creare una soluzione con un progetto.<br />2.  Aggiungere solo soluzione al controllo del codice sorgente come selezione. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />3.  Chiudere la soluzione.<br />4.  Creare una nuova soluzione.<br />5.  Aggiungere la soluzione in precedenza controllata dal controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**\).|`Result from Step 2:`<br /><br /> Progetto non è incluso nel controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> Se la prima soluzione dispone di elementi di soluzione, non possono essere aggiunti dal controllo del codice sorgente, pertanto non verranno visualizzati.<br /><br /> Progetto da prima soluzione verrà visualizzato come non disponibile.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)