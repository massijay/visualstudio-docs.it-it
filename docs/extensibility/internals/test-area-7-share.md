---
title: "Test Area 7: condivisione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], la condivisione di elementi"
  - "origine plug-in del controllo, la condivisione di elementi"
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Test Area 7: condivisione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella regione di esempio che condividono gli elementi tra le posizioni tramite il comando di **condivisione** .  
  
 Un'operazione di hhare è la duplicazione comprensione dei file e gli elementi della cartella tra due o più percorsi all'interno di una gerarchia del file controllo del codice sorgente.  La duplicazione in realtà non avviene sul server, ma riceverà lo stesso file due o più nei percorsi specificati.  Ogni volta che vengono apportate modifiche a uno degli elementi condivisi, tali modifiche vengono visualizzati in qualsiasi altra percorsi condivisi.  
  
 Condividendo le cartelle funziona se si seleziona una cartella con almeno un file nel controllo del codice sorgente in.  Il comando di condivisione è disabilitato nelle seguenti circostanze:  
  
-   se la cartella selezionata è una cartella vuota.  
  
-   Se c " è una cartella effettivo, ma non contiene file del controllo del codice sorgente.  
  
-   Se c " è una cartella virtuale, se i file inclusi nel controllo del codice sorgente sono in o meno.  
  
-   Se c " è un progetto Web del sito remoto.  
  
## Menu Access di comando  
 I seguenti percorsi del menu dell'ambiente di sviluppo integrato di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati nei test case.  
  
 condivisione: **file**\- \>**Controllo del codice sorgente**\- \>**condivisione**.  
  
## comportamento previsto  
  
-   Il file condiviso viene visualizzato nella posizione condivisa.  
  
-   Visualizzando la cronologia dell'archivio della versione del controllo del codice sorgente mostra che i file sono condivisi.  
  
-   Modificando un file condiviso modifica entrambi i percorsi di file.  
  
## Test case  
 Di seguito sono illustrati i test case specifici per l'area esempio di condivisione.  
  
|Azione|Passi del test|I risultati previsti da verificarsi|  
|------------|--------------------|-----------------------------------------|  
|Condividere un file da un progetto caricato nel controllo del codice sorgente in un altro progetto caricato|1.  Creare un nuovo progetto.<br />2.  Aggiungere un secondo progetto alla soluzione.<br />3.  Creare un file nel secondo progetto con un nome che non è in primo progetto.<br />4.  Aggiungere la soluzione al controllo del codice sorgente.<br />5.  selezionare il primo progetto.<br />6.  aprire la finestra di dialogo di **condivisione** \(**file** \- \> **Controllo del codice sorgente** \- \> **condivisione**\).<br />7.  Condividere il file dal secondo progetto al primo progetto.<br />8.  Accettare **Estrai** se necessario.|Comportamento previsto di uso comune.|  
|Condividere un file da un progetto a un altro|1.  Creare un nuovo progetto.<br />2.  Inclusa.<br />3.  chiudere la soluzione.<br />4.  creare un secondo progetto \(nuova soluzione.\)<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  selezionare il progetto.<br />7.  aprire la finestra di dialogo di **condivisione** \(**file** \- \> **Controllo del codice sorgente** \- \> **condivisione**\).<br />8.  Condividere un file dal progetto precedentemente aggiunto al progetto aperto.<br />9. Accettare **Estrai** se necessario.|Comportamento previsto di uso comune.|  
|Condividere una parte del file non del progetto dal controllo del codice sorgente del progetto attualmente caricato|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file al controllo del codice sorgente che non fa parte del progetto o di soluzione.<br />4.  selezionare il progetto e aprire la finestra di dialogo di **condivisione** \(**file** \- \> **Controllo del codice sorgente** \- \> **condivisione**\).<br />5.  Selezionare un file nella finestra di dialogo di **condivisione** che non esiste nel progetto o di soluzione corrente e non la condivisione dei tipi.<br />6.  Accettare **Estrai** se necessario.|L'archivio di controllo del codice sorgente è stata eseguita una ottenere, pertanto il file si trova nel percorso locale del progetto.|  
|Condividere i file nello stesso progetto in una cartella diversa|1.  **Estrai automaticamente** selezionato in **strumenti** \- \> **opzioni** \- \> **Controllo del codice sorgente**.<br />2.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />3.  Aggiungere una cartella al progetto.<br />4.  Aggiungere un file alla cartella di ed è archiviato nella cartella.<br />5.  selezionare la cartella.<br />6.  aprire la finestra di dialogo di **condivisione** \(**file** \- \> **Controllo del codice sorgente** \- \> **condivisione**\).<br />7.  Condividere il file nella cartella selezionata.|Comportamento previsto di uso comune.<br /><br /> La cartella deve essere archiviata con un file in prima di poter essere utilizzata per la condivisione.|  
|Condividere una cartella nel progetto caricato \- ricorsivo|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  selezionare il progetto.<br />4.  aprire la finestra di dialogo di **condivisione** \(**file** \- \> **Controllo del codice sorgente** \- \> **condivisione**\).<br />5.  selezionare una cartella.<br />6.  Condividere la cartella in modo ricorsivo nel progetto.|Comportamento previsto di uso comune.|  
|Condividere diversi file da un progetto a un altro|1.  Creare un nuovo progetto con molti file in.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  chiudere la soluzione.<br />4.  creare un nuovo progetto in una nuova soluzione.<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  selezionare il progetto.<br />7.  aprire la finestra di dialogo di **condivisione** \(**file** \- \> **Controllo del codice sorgente** \- \> **condivisione**\).<br />8.  Condividere diversi file dal progetto creato in precedenza al progetto aperto.|Comportamento previsto di uso comune.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)