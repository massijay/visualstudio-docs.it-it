---
title: "Limitazioni del debug di WCF | Microsoft Docs"
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
  - "debug, WCF"
  - "WCF, limitazioni del debug"
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Limitazioni del debug di WCF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sono disponibili tre modalità per avviare il debug di un servizio WCF:  
  
-   Si esegue il debug di un processo client che chiama un servizio.  Il debugger esegue le istruzioni del servizio.  Il servizio non deve essere presente nella stessa soluzione dell'applicazione client.  
  
-   Si esegue il debug di un processo client che effettua una richiesta a un servizio.  Il servizio deve essere parte della soluzione.  
  
-   Si utilizza **Connetti a processo** per la connessione a un servizio attualmente in esecuzione.  Il debug inizia all'interno del servizio.  
  
 In questo argomento vengono descritte le limitazioni di questi scenari.  
  
## Limitazioni dell'esecuzione di istruzioni in un servizio  
 Per eseguire istruzioni in un servizio da un'applicazione client di cui si esegue il debug, è necessario soddisfare le seguenti condizioni:  
  
-   Il client deve chiamare il servizio utilizzando un oggetto client sincrono.  
  
-   L'operazione del contratto non può essere unidirezionale.  
  
-   Se il server è asincrono, non è possibile visualizzare lo stack di chiamate completo durante l'esecuzione del codice nel servizio.  
  
-   È necessario abilitare il debug con il codice riportato di seguito nel file app.config o web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     È necessario aggiungere questo codice solo una volta.  È possibile aggiungere il codice modificando il file con estensione config o attraverso la connessione al servizio utilizzando **Connetti a processo**.  Quando si utilizza **Connetti a processo** in un servizio, il codice di debug viene aggiunto automaticamente al file config.  Successivamente, è possibile eseguire il debug e le istruzioni nel servizio senza dover modificare il file config.  
  
## Limitazioni dell'uscita da un servizio  
 L'uscita da un servizio e il ritorno al client presenta le stesse limitazioni descritte per l'esecuzione delle istruzioni di un servizio.  Inoltre, il debugger deve essere connesso al client.  Se è in corso il debug di un client e l'esecuzione di istruzioni in un servizio, il debugger rimane connesso al servizio.  Ciò si applica sia che il client venga avviato utilizzando **Avvia debug** sia che ci si connetta al client utilizzando **Connetti a processo**.  Se il debug è stato avviato mediante la connessione al servizio, il debugger non è ancora connesso al client.  In tal caso, se occorre uscire dal servizio e tornare al client, è innanzitutto necessario utilizzare **Connetti a processo** per la connessione manuale al client.  
  
## Limitazioni della connessione automatica a un servizio  
 La connessione automatica a un servizio presenta le limitazioni riportate di seguito:  
  
-   Il servizio deve essere parte della soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di cui si esegue il debug.  
  
-   Il servizio deve essere ospitato.  Può essere parte di un progetto di sito Web \(File system e HTTP\), un progetto di applicazione Web \(File system e HTTP\) o un progetto di libreria di servizi WCF.  I progetti di libreria di servizi WCF possono essere librerie di servizi o librerie di servizi di flusso di lavoro.  
  
-   Il servizio deve essere richiamato da un client WCF.  
  
-   È necessario abilitare il debug con il codice riportato di seguito nel file app.config o web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## Self\-hosting  
 Un *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, nell'host dei servizi WCF o nel server di sviluppo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Per informazioni su come eseguire il debug di un servizio self\-hosted, vedere [Procedura: eseguire il debug di un servizio WCF indipendente](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## Self\-hosting  
 Per abilitare il debug delle applicazioni di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, è necessario installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5 prima dell'installazione di [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  Se [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] viene installato prima di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, quando si tenta di eseguire il debug di un'applicazione di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5 viene generato un errore.  Il messaggio di errore è "Impossibile eseguire automaticamente l'istruzione sul server". Per correggere questo problema, utilizzare il **Pannello di controllo** di Windows, scegliere **Programmi e funzionalità** per ripristinare l'installazione di [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
## Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Procedura: eseguire il debug di un servizio WCF indipendente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)