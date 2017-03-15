---
title: "Procedura: eseguire il debug di un servizio WCF indipendente | Microsoft Docs"
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
  - "WCF, debug"
  - "WCF, servizio indipendente"
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Procedura: eseguire il debug di un servizio WCF indipendente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un *servizio indipendente* è un servizio WCF che non viene eseguito in IIS, nell'host dei servizi WCF o nel server di sviluppo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  La modalità più semplice per eseguire il debug di un servizio WCF indipendente è configurare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in modo che vengano avviati client e server quando si sceglie **Avvia debug** dal menu **Debug**.  
  
 Se il servizio WCF è indipendente o è un processo che non può essere avviato in questa modalità, ad esempio un servizio NT, non è possibile utilizzare questo metodo.  È possibile invece effettuare una delle seguenti operazioni:  
  
-   Connettere manualmente il debugger al processo di hosting.  Per ulteriori informazioni, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     —oppure—  
  
-   Avviare il debug del client e quindi eseguire istruzioni nella chiamata al servizio.  Richiede l'attivazione del debug nel file app.config.  Per ulteriori informazioni, vedere [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Per avviare client e host da Visual Studio  
  
1.  Creare una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente entrambi i progetti client e server.  
  
2.  Configurare la soluzione in modo che quando si sceglie **Avvia** dal menu **Debug** vengano avviati entrambi i processi client e server.  
  
    1.  Fare clic con il pulsante destro del mouse sul nome della soluzione in **Esplora soluzioni**.  
  
    2.  Fare clic su **Imposta progetti di avvio**.  
  
    3.  Nella finestra di dialogo **Proprietà di \<nome\> soluzione** selezionare l'opzione **Progetti di avvio multipli**.  
  
    4.  Nella griglia **Progetti di avvio multipli**, nella riga che corrisponde al progetto server fare clic su **Azione** e scegliere **Avvia**.  
  
    5.  Nella riga che corrisponde al progetto client fare clic su **Azione** e scegliere **Avvia**.  
  
    6.  Fare clic su **OK**.  
  
## Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Procedura: eseguire istruzioni nei servizi WCF](../debugger/how-to-step-into-wcf-services.md)