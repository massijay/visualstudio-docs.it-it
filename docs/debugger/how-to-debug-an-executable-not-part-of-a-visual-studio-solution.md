---
title: "Procedura: eseguire il debug di un eseguibile non incluso in una soluzione di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], eseguibili"
  - "file eseguibili, debug della parte esterna dei progetti"
  - "file eseguibili, importazione"
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il debug di un eseguibile non incluso in una soluzione di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Talvolta può essere necessario eseguire il debug di un file eseguibile non incluso in un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)],  ossia di un eseguibile creato all'esterno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o ricevuto da un altro sviluppatore.  
  
 In questi casi, normalmente si avvia l'eseguibile all'esterno di Visual Studio e ci si connette al processo in esecuzione utilizzando il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere[Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Per connettersi a un'applicazione è necessario eseguire delle operazioni manuali che richiedono alcuni secondi.  A causa di questo minimo ritardo, la connessione non risulterà utile se si tenta di eseguire il debug di un problema verificatosi in fase di avvio.  Se inoltre si esegue il debug di un programma che non richiede input da parte dell'utente e che termina rapidamente, il tempo necessario per eseguire la connessione potrebbe non essere disponibile.  Se si è installato [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], è possibile creare un progetto EXE per tale programma.  
  
### Per creare un progetto EXE per un eseguibile esistente  
  
1.  Scegliere **Apri** dal menu **File**, quindi **Progetto**.  
  
2.  Nella finestra di dialogo **Apri progetto** fare clic sull'elenco a discesa **Nome file** e selezionare **Tutti i file del progetto**.  
  
3.  Individuare l'eseguibile e scegliere **OK**.  
  
     In questo modo verrà creata una soluzione temporanea contenente l'eseguibile.  
  
### Per importare un eseguibile in una soluzione di Visual Studio  
  
1.  Scegliere **Aggiungi progetto** dal menu **File**, quindi fare clic su **Progetto esistente**.  
  
2.  Nella finestra di dialogo **Aggiungi progetto esistente** fare clic sull'elenco a discesa **Nome file** e selezionare **Tutti i file del progetto**.  
  
3.  Individuare e selezionare l'eseguibile.  
  
4.  Scegliere **OK**.  
  
5.  Avviare l'eseguibile scegliendo un comando, ad esempio **Avvia**, dal menu **Debug**.  
  
    > [!NOTE]
    >  I progetti EXE non sono supportati da tutti i linguaggi di programmazione.  Se è necessario utilizzare questa funzionalità, installare [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
     Quando si effettua il debug di un eseguibile senza il codice sorgente, le funzionalità di debug disponibili sono limitate, indipendentemente dal fatto che si stabilisca una connessione a un eseguibile in esecuzione o che si aggiunga l'eseguibile a una soluzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se l'eseguibile è stato compilato senza informazioni di debug in un formato compatibile, le funzionalità disponibili risulteranno ulteriormente limitate.  Se si dispone del codice sorgente, l'approccio migliore consiste nell'importarlo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e nel creare una build di debug dell'eseguibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [DBG Files](http://msdn.microsoft.com/it-it/91e449e9-8b65-4123-960f-2107cd1f1cfd)