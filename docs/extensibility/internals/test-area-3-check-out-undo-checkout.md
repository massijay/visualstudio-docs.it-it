---
title: "Area test 3: Controllo out-Annulla estrazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plug-in del controllo codice sorgente, estrazione"
  - "annullare l'estrazione, plug-in del controllo del codice sorgente"
  - "controllo del codice sorgente [Visual Studio SDK], estrazione"
  - "annullamento dell'estrazione [Visual Studio SDK], controllo di origine"
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Area test 3: Estrazione / Annulla estrazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa area di plug\-in test di controllo del codice sorgente vengono illustrati gli elementi di modifica e di ripristino dall'archivio versione tramite il **estrazione** e **Annulla estrazione** i comandi.  
  
 **Estrazione**: i segni di un elemento nell'archivio delle versioni come estratto, modifica la copia locale di lettura\/scrittura.  
  
 **Annulla estrazione**: contrassegnare gli elementi nell'archivio delle versioni come archiviato, viene ripristinata la copia locale allo stato di check\-out \(a seconda delle opzioni\).  
  
## Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi di menu dell'ambiente di sviluppo integrato nei test case.  
  
##### Vedere:  
  
-   **File**, **controllo del codice sorgente**, **estrazione**.  
  
-   **File**, **estrazione**.  
  
-   Menu di scelta rapida, **estrazione**.  
  
-   Annullamento estrazione: **File**, **controllo del codice sorgente**, **Annulla estrazione**.  
  
## Comportamento previsto comune  
  
-   Dopo l'operazione di estrazione, il file di destinazione e\/o le cartelle sono contrassegnate come estratti nell'archivio delle versioni.  
  
-   L'archivio versione attributi utente corretto l'estrazione.  
  
-   La data dell'estrazione e l'ora siano corrette \(per le impostazioni dell'utente\).  
  
## Test case  
 Di seguito sono specifici test case per l'area di test di estrazione\/annullamento dell'estrazione.  
  
### Caso 3: estrazione  
 In questa sezione è incentrata sul funzionamento del comando di estrazione.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Controllare le esclusivo \(COE\) un progetto client|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrae l'intero progetto in modo esclusivo \(**File**, **estrazione**\).|Si verifica l'estrazione.|  
|Estrazione esclusiva \(COE\) un File System o un progetto Web IIS locale|1.  Impostare connessione Server Web per la condivisione nel File **strumenti**, **Opzioni**, **progetti**, **impostazioni Web**.<br />2.  Creare un progetto Web.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrae l'intero progetto in modo esclusivo \(**File**, **controllo del codice sorgente**, **estrazione**\).|Si verifica l'estrazione.|  
|Controllare gli elementi di soluzione in una soluzione \(nuovo metodo per la gestione di altri file\)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre la soluzione.<br />4.  Aggiungere diversi elementi di soluzione.<br />5.  Controllare tutti gli elementi appena aggiunti.<br />6.  Selezionare più elementi di soluzione.<br />7.  Estrae gli elementi selezionati \(Menu di scelta rapida, **estrazione**\).|Sono stati estratti i file selezionati.|  
|Estrai versione locale \(se questa funzionalità supporta i plug\-in sottoposta a test\)|1.  L'utente 1: Creare un progetto client.<br />2.  L'utente 1: Aggiungere la soluzione al controllo del codice sorgente.<br />3.  L'utente 2: Aprire la soluzione dal controllo del codice sorgente in un altro percorso.<br />4.  L'utente 2: Estrarre un file.<br />5.  L'utente 2: Modificare il file.<br />6.  L'utente 2: Archiviare il file.<br />7.  L'utente 1: Verificare la versione locale del file \(controllare il **Estrai versione locale** nell'opzione avanzata **Check Out** la finestra di dialogo\).|La versione locale del file è estratto.<br /><br /> Le modifiche apportate dall'utente 2 non vengono applicate al file utente 1.|  
  
### Caso 3b: disconnesso, vedere  
 In modalità disconnessa consente agli utenti un certo livello di supporto per il controllo origine ripetuti quando non è associato direttamente a un archivio delle versioni. Ciò avviene memorizzando localmente tutte le informazioni rilevanti sui progetti e soluzioni integrate.  
  
 Operazioni di estrazione esclusiva può verificarsi solo durante la connessione all'archivio di controllo di origine. Operazioni di estrazione condivisa può verificarsi in qualsiasi momento, se connessi o disconnessi. Pertanto, quando disconnesso dall'archivio versione, solo il **controllare e condiviso** \(CO\) comando è abilitato. Quando si è disconnessi, **Annulla estrazione** è disabilitato perché la versione precedente non può essere recuperata per sostituire le modifiche apportate dall'utente.  
  
 Quando l'utente si riconnette alla versione archiviare, gli stati di estrazione di tutte le soluzioni integrate e i progetti vengono sincronizzati. Per le estrazioni che l'utente ha eseguito l'operazione che esegue gli aggiornamenti necessari per l'archivio. Una volta che si è verificata la sincronizzazione, l'utente è in grado di continuare a lavorare normalmente \(connesso\).  
  
#### Comportamento previsto  
  
-   Impossibile utilizzare **Out esclusivamente** comando durante la disconnessione dall'archivio versione.  
  
-   Impossibile utilizzare **Annulla estrazione** comando durante la disconnessione dall'archivio versione.  
  
-   **Condivisi Check Out** comando works.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Durante la disconnessione, estrarre un file, quindi connettersi per la sincronizzazione|1.  Disconnettere un progetto controllato tramite la finestra di dialogo Modifica controllo del codice sorgente \(**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**l\).<br />2.  Estrarre un file.<br />3.  Fare clic su Estrai \(disconnesso\) nella finestra di dialogo di avviso.<br />4.  Modificare il file.<br />5.  Connettersi utilizzando la finestra di dialogo Modifica controllo del codice sorgente.<br />6.  Ottenere la versione più recente del file modificato.|Comportamento previsto comune|  
  
### Caso 3c: Query o modifica Query Salva \(QEQS\)  
 Gli elementi nel controllo del codice sorgente vengono tenuta traccia per le modifiche, le modifiche, e Salva per consentire agli utenti facilmente gestione i file. Quando viene modificato un elemento controllato "archiviato", QEQS intercetta la modifica di tentata e chiede all'utente se desidera estrarre il file per modificarlo. In base alle **strumenti**, **Opzioni** impostazioni, l'utente è obbligati a verificare il file in uscita per modificare o possono essere autorizzati a modificare una copia in memoria e check\-out in un secondo momento. Se l'utente **strumenti**, **Opzioni** non è impostata per visualizzare la finestra di dialogo di estrazione e appena estrarlo, quindi effettua la modifica, il file viene automaticamente estratto, ogni volta che è possibile.  
  
#### Comportamento previsto  
  
-   Dopo l'operazione di estrazione, il file di destinazione e\/o le cartelle sono contrassegnate come estratti nell'archivio delle versioni.  
  
-   L'archivio versione attributi di check\-out per l'utente corretto.  
  
-   La data di check\-out e l'ora siano corrette \(per le impostazioni dell'utente\).  
  
-   La copia locale del file di destinazione o della cartella è scrivibile.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Modificare i file di testo che viene controllato|1.  Creare un nuovo progetto contenente un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Impostare **strumenti**, **Opzioni**, **controllo del codice sorgente**, **consentire la modifica di sola lettura su disco dei file** a deselezionata.<br />4.  Impostare **strumenti**, **Opzioni**, **controllo del codice sorgente**, **Richiedi estrazione** nel **Quando archiviato i file vengono modificati** casella combinata.<br />5.  Impostare **strumenti**, **Opzioni**, **controllo del codice sorgente**, **Richiedi estrazione** nel **Quando archiviare i file vengono salvati** casella combinata.<br />6.  Aprire il file di testo nell'editor, tentare di digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />7.  Fare clic su **Annulla** nel **Estrai per la modifica** la finestra di dialogo. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />8.  Impostare **strumenti**, **Opzioni**, **controllo del codice sorgente**, **consentire la modifica di sola lettura su disco dei file** a selezionato.<br />9. Aprire il file di progetto nell'editor, tentare di digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />10. Fare clic su **modificare** nel **Estrai per la modifica** la finestra di dialogo. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />11. Modificare il file di testo e tenta di salvarlo.|`Result of step 6:`<br /><br /> Estrarre per viene visualizzata la finestra di dialogo di modifica.<br /><br /> `Result of step 7:`<br /><br /> Il file rimane invariato.<br /><br /> `Result of step 9:`<br /><br /> Estrarre per viene visualizzata la finestra di dialogo di modifica.<br /><br /> `Result of step 10:`<br /><br /> È possibile modificare il file di progetto in memoria.<br /><br /> `Result of step 11:`<br /><br /> Salva l'estrazione in Salva la finestra di dialogo viene visualizzato.|  
|Modificare un file di soluzione che viene controllato|Ripetere i passaggi come descritto nella precedente test ma anziché modificare un file di testo, modificare soluzione modificando le proprietà di soluzione.|Come test precedente|  
|Modificare un file di progetto che viene controllato|Ripetere i passaggi come descritto nella precedente test ma anziché modificare un file di testo, Modifica progetto modificando le proprietà del progetto.|Come test precedente.|  
  
### Caso 3d: Estrazione automatica  
 Questo controllo include sottoarea su scenari in cui il **estrazione** la finestra di dialogo non viene visualizzato per ogni utente **strumenti**, **Opzioni**, **le impostazioni di controllo del codice sorgente**.  
  
#### Comportamento previsto  
  
-   Dopo l'operazione di estrazione, il file di destinazione e\/o le cartelle sono contrassegnate come estratti nell'archivio delle versioni.  
  
-   L'archivio versione attributi di check\-out per l'utente corretto.  
  
-   La data e ora dell'estrazione è corretto \(per le impostazioni dell'utente\).  
  
-   La copia locale del file di destinazione o della cartella è scrivibile.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Estrazione automatica di un file|1.  Impostare **strumenti**, **Opzioni**, **controllo del codice sorgente** a **file di checkpoint automaticamente su edit**.<br />2.  Creare un nuovo progetto con un file.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrarre il file.|File viene estratto automaticamente \(senza interfaccia utente\).|  
|Estrazione invisibile all'utente per un progetto|1.  Impostare **strumenti**, **Opzioni**, **controllo del codice sorgente** a **file di checkpoint automaticamente su edit**.<br />2.  Creare un nuovo progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrarre il progetto.|File viene estratto automaticamente \(senza interfaccia utente\).|  
  
### Caso 3e: Annulla estrazione  
 **Annulla estrazione** viene utilizzato per annullare un file estratto stato ed evitare di archiviare modifiche apportate al file.  
  
#### Comportamento previsto  
  
-   Il valore predefinito si basa l'utente **estrae la versione locale** impostazione. Se l'utente ha scelto di estrarre la versione locale, il valore predefinito per l'annullamento dell'estrazione consiste nel ripristinare la versione estratta.  
  
-   Una volta accettato l'operazione di annullamento, le icone in **Esplora soluzioni** vengono aggiornate per i file e l'elemento viene rimosso dal **Archiviazioni in sospeso** finestra.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Annullare l'estrazione di un singolo file che è stato estratto in modo esclusivo|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrae un file in modo esclusivo.<br />4.  Modificare il file.<br />5.  Annulla estrazione \(**File**, **controllo del codice sorgente**, **Annulla estrazione**\).|Comuni al comportamento previsto.|  
|Annullare l'estrazione di un singolo file che è stato estratto condiviso|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre un file condiviso.<br />4.  Modificare il file.<br />5.  Annulla estrazione \(**File**, **controllo del codice sorgente**, **Annulla estrazione**\).|Comuni al comportamento previsto.|  
|Annullare l'estrazione di un progetto dopo l'aggiunta di file al progetto|1.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2.  Estrarre il progetto.<br />3.  Aggiungere un file al progetto.<br />4.  Annullare l'estrazione del progetto.|Aggiunta di file viene rimosso dal progetto in Esplora soluzioni.<br /><br /> Progetto non è stato estratto.|  
|Annullare l'estrazione di un progetto dopo l'eliminazione di file dal progetto|1.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2.  Estrarre il progetto.<br />3.  Eliminare un file dal progetto.<br />4.  Annullare l'estrazione del progetto.|File eliminato viene visualizzato sotto il progetto in Esplora soluzioni.<br /><br /> Progetto non è stato estratto.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)