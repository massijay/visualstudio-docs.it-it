---
title: "Test Area 4: Check- | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], archiviazione di elementi"
  - "estrazione degli elementi origine controllo plug-in,"
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Test Area 4: Check-
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questo settore plug\-in test di controllo del codice sorgente riguarda l'invio di elementi aggiornati all'archivio delle versioni tramite il **Archivia** comando.  
  
## Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono utilizzati percorsi di menu dell'ambiente di sviluppo integrato nei test case.  
  
##### Archiviare:  
 **File**, **controllo del codice sorgente**, **Archivia**.  
  
 **File**, **Archivia**.  
  
 Menu di scelta rapida, **Archivia**.  
  
## Comportamento previsto comune  
  
-   Progetti e i file aggiunti a una soluzione o un progetto nel controllo del codice sorgente vengono visualizzati di **Archivia** la finestra di dialogo e **Archiviazioni in sospeso** finestra.  
  
-   Dopo il check\-in, gli elementi aggiunti vengono visualizzati nel controllo del codice sorgente.  
  
-   Dopo il check\-in, gli elementi aggiornati vengono utilizzate versioni correttamente nell'archivio.  
  
## Test case  
 Di seguito sono specifici test case per l'area di test di archiviazione.  
  
### Caso 4: modificare elementi  
 Viene descritto l'utilizzo di controllo in azione per aggiornare un file di controllo del codice sorgente che è stato modificato.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Modificare un file di testo che è stato estratto, archiviare solo i file \(**Archivia** la finestra di dialogo\)|1.  Creare un nuovo progetto con un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre e modificare il file di testo.<br />4.  Archiviazione tramite la finestra di dialogo Archivia \(**File**, **controllo del codice sorgente**, **Archivia**\).|Comuni al comportamento previsto.|  
|Modificare un file di testo che è stato estratto, archiviare solo i file \(**Archiviazioni in sospeso** finestra\)|1.  Creare un nuovo progetto con un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre e modificare il file di testo.<br />4.  Archiviare tramite il **Archiviazioni in sospeso** finestra.|Comuni al comportamento previsto.|  
  
### Caso 4b: aggiunta di file  
 Quando si aggiunge un file a un progetto o un elemento a una soluzione, necessario modificare anche il progetto o soluzione. In questo modo il file principale viene estratto anche e deve essere archiviato per completare l'aggiunta.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Aggiungere un file di testo e archivia i file \(**Archivia** la finestra di dialogo\)|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file di testo al progetto.<br />4.  Se richiesto, accettare estrazione del progetto.<br />5.  Selezionare la soluzione in **Esplora**.<br />6.  Archivia dal **Archivia** la finestra di dialogo.|Comuni al comportamento previsto.|  
|Aggiungere un file di testo e archivia i file \(**Archiviazioni in sospeso** finestra\)|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file di testo al progetto.<br />4.  Se richiesto, accettare estrazione del progetto.<br />5.  Controllare nella soluzione da **Archiviazioni in sospeso** finestra.|Comportamento previsto comune|  
  
### Caso 4c: aggiunta di progetti  
 Quando si aggiunge un progetto a una soluzione, necessario modificare anche la soluzione. In questo modo il file di soluzione inoltre estratto e deve essere archiviato per completare l'aggiunta.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente \(**Archivia** la finestra di dialogo\)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto.<br />4.  Se richiesto, accettare estrazione della soluzione.<br />5.  Archivia dal **Archivia** la finestra di dialogo.|Comuni al comportamento previsto.|  
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente \(**Archiviazioni in sospeso** finestra\)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto.<br />4.  Se richiesto, accettare estrazione della soluzione.<br />5.  Controllare nella soluzione da **Archiviazioni in sospeso** finestra.|Comuni al comportamento previsto.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)