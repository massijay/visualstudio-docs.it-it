---
title: "Procedura: Specificare comandi pre- e post-strumentazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.instrument"
helpviewer_keywords: 
  - "strumenti per la profilatura, eventi pre-strumentazione"
  - "eventi [Visual Studio LightSwitch], pre-strumentazione"
  - "eventi pre-strumentazione, strumenti per le prestazioni"
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Specificare comandi pre- e post-strumentazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile specificare comandi da eseguire prima o dopo che vengano instrumentati i file binari in una sessione di prestazioni.  I comandi che possono essere eseguiti dalla riga di comando possono essere specificati come eventi pre\-strumentazione o post\-strumentazione.  Ad esempio, è possibile specificare comandi che automatizzano la riapposizione della firma di un assembly con una chiave con nome sicuro in un file batch eseguito dopo la strumentazione dei binari.  
  
 È possibile specificare comandi per tutti i binari instrumentati nell'esecuzione della profilatura o per singoli binari.  È tuttavia possibile specificare un solo comando pre\-strumentazione da eseguire prima e un solo comando post\-strumentazione da eseguire dopo il processo di strumentazione.  Non è possibile specificare comandi sia per tutti i binari che per singoli binari.  Quando si specificano comandi per tutti i binari, i comandi vengono eseguiti prima o dopo la strumentazione di ogni binario della sessione.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 La directory di lavoro nella quale vengono eseguiti i comandi dipende dal sistema operativo su cui è in esecuzione [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] e sulla piattaforma di destinazione dell'applicazione profilata.  
  
 **Computer a 32 bit**  
  
 Nei computer a 32 bit la directory degli strumenti del profiler predefinita è Unità\\Programmi\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools.  
  
 **Computer a 64 bit**  
  
 Nei computer a 64 bit specificare il percorso in base alla piattaforma di destinazione dell'applicazione profilata:  
  
-   Per le applicazioni a 32 bit, la directory degli strumenti del profiler predefinita è:  
  
     *Drive*\\Programmi \(x86\)\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools  
  
-   Per le applicazioni a 64 bit, la directory degli strumenti del profiler predefinita è:  
  
     *Drive*\\Programmi \(x86\)\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools\\x64  
  
### Per specificare i comandi pre\-strumentazione  
  
1.  Effettuare uno dei passaggi riportati di seguito.  
  
    -   Per specificare comandi pre\-strumentazione per tutti i binari di una sessione di prestazioni, selezionare il nodo della sessione di prestazioni in **Esplora prestazioni**, quindi fare clic con il pulsante destro del mouse e scegliere **Proprietà**.  
  
    -   Per specificare i comandi di pre\-strumentazione per un file binario specifico, fare clic con il pulsante destro del mouse sul nome del file binario nell'elenco **Destinazioni** della sessione di prestazioni, quindi scegliere **Proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic su **Strumentazione**.  
  
3.  In **Eventi pre\-strumentazione** digitare il comando nella casella di testo **Riga di comando**.  
  
    > [!NOTE]
    >  È possibile fare clic sul pulsante con i puntini di sospensione **\(…\)** accanto alla casella **Riga di comando** per individuare e selezionare il file exe, cmd o bat appropriato.  
  
4.  Scegliere **OK**.  
  
     Per impedire l'esecuzione del comando senza rimuoverlo, selezionare la casella di controllo **Escludere dalla strumentazione**.  Per modificare le impostazioni del compilatore o del linker, utilizzare le pagine delle proprietà del progetto.  
  
### Per specificare i comandi post\-strumentazione  
  
1.  Effettuare uno dei passaggi riportati di seguito.  
  
    -   Per specificare comandi di post\-strumentazione per tutti i file binari in una sessione di prestazioni, selezionare il nodo della sessione di prestazioni in **Esplora prestazioni** e quindi fare clic con il pulsante destro del mouse e scegliere **Proprietà**.  
  
    -   Per specificare i comandi post\-strumentazione per un binario specifico, fare clic con il pulsante destro del mouse sul nome del binario nell'elenco **Destinazioni** della sessione di prestazioni, quindi selezionare **Proprietà**.  
  
2.  In **Pagine delle proprietà** fare clic su **Strumentazione**.  
  
3.  In **Eventi post\-strumentazione** digitare il comando nella casella di testo **Riga di comando**.  
  
    > [!NOTE]
    >  È possibile fare clic sul pulsante con i puntini di sospensione **\(…\)** accanto alla casella **Riga di comando** per individuare e selezionare il file exe, cmd o bat appropriato.  
  
4.  Scegliere **OK**.  
  
     Per impedire l'esecuzione del comando senza rimuoverlo, selezionare la casella di controllo **Escludere dalla strumentazione**.  Per modificare le impostazioni del compilatore o del linker, utilizzare le pagine delle proprietà del progetto.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)