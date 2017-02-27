---
title: "Procedura: Limitare la strumentazione a specifiche DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, finestra di controllo della profilatura in fase di esecuzione"
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: Limitare la strumentazione a specifiche DLL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite il metodo di analisi strumentazione, è possibile limitare la raccolta dei dati di analisi a una o più DLL di un'applicazione.  Per profilare una o più DLL di un'applicazione, creare una sessione di prestazioni che includa i file con estensione dll come destinazioni.  È possibile specificare le DLL da profilare come progetti in una soluzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o come file binari indipendenti.  
  
### Per limitare la strumentazione alle DLL specifiche di una soluzione di Visual Studio  
  
1.  Aprire la soluzione contenente la DLL in [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Dal menu **Analizza** scegliere **Avvia Creazione guidata sessione di prestazioni**.  
  
3.  Scegliere **Strumentazione** come metodo di analisi, quindi fare clic su **Avanti**.  
  
4.  In **Specificare le destinazioni da profilare** selezionare il nome del progetto con estensione dll, quindi scegliere **Avanti**.  
  
5.  Fare clic su **Fine** per uscire dalla procedura guidata e visualizzare la nuova sessione di prestazioni nella finestra **Esplora prestazioni** .  
  
6.  Fare clic con il pulsante destro del mouse su **Destinazioni** e quindi scegliere **Aggiungi progetto di destinazione**.  
  
7.  Dall'elenco **Aggiungi progetto di destinazione** , selezionare il progetto eseguibile che si desidera utilizzare per verificare la DLL.  
  
     Opzionale.  È possibile aggiungere qualsiasi progetto DLL che si desidera profilare.  
  
8.  Per impedire la raccolta di dati per un progetto aggiunto, fare clic con il pulsante destro del mouse sul nome del progetto, quindi deselezionare la casella di controllo **Strumento**.  
  
### Per specificare determinate DLL da profilare come file binari indipendenti  
  
1.  Aprire [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
2.  Dal menu **Analizza** scegliere **Avvia Creazione guidata sessione di prestazioni**.  
  
3.  In **Specificare le destinazioni da profilare** selezionare **Profilatura di una libreria a collegamento dinamico \(.DLL\)**, quindi scegliere **Avanti**.  
  
4.  Nella seconda pagina della procedura guidata, eseguire i passaggi seguenti:  
  
    -   Digitare il percorso e il nome del file con estensione dll da profilare in **Percorso DLL**.  È anche possibile fare clic sul pulsante con i puntini di sospensione \(...\) per individuare il file nella finestra di dialogo **Libreria a collegamento dinamico da profilare** .  Si noti che è necessario specificare la copia del file con estensione dll che verrà avviato dal file eseguibile \(exe\) che si seleziona al passaggio successivo.  
  
    -   Digitare il percorso e il nome del file eseguibile \(.exe\) che verrà utilizzato per verificare il file con estensione dll in **Percorso eseguibile**.  È anche possibile fare clic sul pulsante con i puntini di sospensione \(...\) per individuare il file nella finestra di dialogo **Eseguibile da avviare** .  
  
    -   Opzionale.  Digitare gli argomenti della riga di comando da passare al file eseguibile in **Argomenti della riga di comando**.  Se necessario, specificare la directory di lavoro per l'applicazione in **Cartella di lavoro**.  
  
    -   Scegliere **Avanti**.  
  
5.  Scegliere **Strumentazione** come metodo di analisi, quindi fare clic su **Avanti**.  
  
6.  Fare clic su **Fine** per uscire dalla procedura guidata e visualizzare la nuova sessione di prestazioni nella finestra **Esplora prestazioni** .  
  
7.  Opzionale.  Per aggiungere più file .dll, fare clic con il pulsante destro del mouse su **Destinazioni** , quindi selezionare **Aggiungi binario di destinazione**.  Selezionare i file dalla finestra di dialogo **Aggiungi binario di destinazione** .  
  
    > [!NOTE]
    >  Non specificare il file eseguibile \(.exe\) che verifica le DLL.  
  
## Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Procedura: Limitare la strumentazione a specifiche funzioni](../profiling/how-to-limit-instrumentation-to-specific-functions.md)