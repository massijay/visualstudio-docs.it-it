---
title: "Area di test 2: Ottenere dal controllo del codice sorgente | Microsoft Docs"
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
  - "controllo del codice sorgente plug-in, il recupero di elementi dal controllo del codice sorgente"
  - "controllo del codice sorgente [Visual Studio SDK], il recupero di elementi da"
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Area di test 2: Ottenere dal controllo del codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa area di test riguarda i test case per il recupero di elementi dall'archivio versione tramite il comando Get. Questi test case possono essere applicati a entrambe locale e ai progetti Web.  
  
## Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi di menu dell'ambiente di sviluppo integrato nei test case.  
  
##### Ottenere la versione più recente:  
  
-   **File**, **controllo del codice sorgente**, **Leggi ultima versione**.  
  
-   **File**, **Leggi ultima versione**.  
  
-   Menu di scelta rapida, **Leggi ultima versione**.  
  
-   Get: **File**, **controllo del codice sorgente**, **ottenere**.  
  
## Comportamento previsto  
  
##### Ottenere la versione più recente:  
 Esegue un recupero invisibile \(alcuna interfaccia utente\) della versione più recente dell'elemento dall'archivio versione.  
  
##### Get:  
 Consente di visualizzare il **ottenere** la finestra di dialogo e consente all'utente di apportare modifiche al set di file che verrà recuperato, nonché modificare le opzioni che influiscono sul modo in cui vengono recuperati i file.  
  
## Test case  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Ottenere la versione più recente di un file che non esiste in locale|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Elimina la copia locale dell'elemento.<br />5.  Ottenere la versione più recente dell'elemento \(Menu di scelta rapida, **Leggi ultima versione**\).|File di elemento viene recuperato in locale.|  
|Ottenere un file che non esiste in locale|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Elimina la copia locale dell'elemento.<br />5.  Ottenere l'elemento \(**File**, **controllo del codice sorgente**, **ottenere** \< elemento \>\).|File di elemento viene recuperato in locale.|  
|Ottenere un file che è stati estratto in modo esclusivo e modificato localmente|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Estrae l'elemento del progetto in modo esclusivo.<br />5.  Modificare la copia locale.<br />6.  Ottenere la versione più recente dell'elemento \(**File**, **Leggi ultima versione di** \< elemento \>\). Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />7.  Fare clic su **sostituire** pulsante nella finestra di dialogo di avviso.|**ReResult dal passaggio 6** `:`<br /><br /> La finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **ReResult ottenuto nel passaggio 7:**<br /><br /> File locali modificato viene sostituita dalla versione originale dall'archivio versione.<br /><br /> File è di lettura\/scrittura.|  
|Ottenere e sostituire i file estratti, condiviso e modificato localmente|1.  Creare un nuovo progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Estrarre l'elemento del progetto come condiviso.<br />5.  Modificare la copia locale.<br />6.  Ottenere la versione più recente dell'elemento \(**File**, **Leggi ultima versione di** \< elemento \>\). Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />7.  Fare clic su **sostituire** nella finestra di dialogo di avviso.|**Risultato del passaggio 6:**<br /><br /> La finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **Risultato ottenuto nel passaggio 7:**<br /><br /> File locali modificato viene sostituita dalla versione originale dall'archivio versione.<br /><br /> File è di lettura\/scrittura.|  
|Ottenere un file che esistono in locale, come la versione più recente nell'archivio delle versioni|1.  Creare un nuovo progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Ottenere l'elemento \(**File**, **controllo del codice sorgente**, **ottenere** \< elemento \>\).|File locale rimane invariato.|  
|Ottenere una soluzione con un progetto|1.  Creare una soluzione con un progetto.<br />2.  Inserire la soluzione nel controllo del codice sorgente.<br />3.  Eliminare tutti i file di progetto in locale.<br />4.  Ottenere la soluzione \(**File**, **controllo del codice sorgente**, **ottenere**\).|Tutti i file eliminati vengono ripristinati in locale.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)