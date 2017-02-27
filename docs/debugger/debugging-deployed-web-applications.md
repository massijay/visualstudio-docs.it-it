---
title: "Debug di applicazioni Web distribuite | Microsoft Docs"
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
  - "applicazioni Web ASP.NET"
  - "ASP.NET, debug di applicazioni Web"
  - "debug di servizi Web"
  - "servizi Web, debug"
  - "servizi Web XML, debug"
  - "XML, debug di servizi Web"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# Debug di applicazioni Web distribuite
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se è necessario eseguire il debug di un'applicazione Web in esecuzione su un server di produzione, è consigliabile procedere con cautela.  In caso di connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] per eseguire il debug e raggiungere un punto di interruzione, ad esempio, tutto il codice gestito nel processo di lavoro si arresta.  L'arresto di tutto il codice gestito nel processo di lavoro può comportare l'arresto del lavoro per tutti gli utenti del server.  Prima di eseguire il debug su un server di produzione, tenere in considerazione il potenziale impatto sulle attività produttive.  
  
 Per utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire il debug di un'applicazione distribuita, è necessario effettuare la connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e verificare che il debugger abbia accesso ai simboli per l'applicazione.  Inoltre, è necessario individuare e aprire i file di origine dell'applicazione.  Per ulteriori informazioni, vedere [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Procedura: individuare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) e [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Molte applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fanno riferimento a DLL contenenti logica di business o altro codice utile.  Tale riferimento consente di copiare automaticamente la DLL dal computer locale alla cartella \\bin della directory virtuale dell'applicazione Web.  Quando si esegue il debug, tenere presente che l'applicazione Web fa riferimento a tale copia della DLL e non alla copia presente sul computer locale.  
  
 La connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è praticamente identica alla connessione a qualsiasi altro processo remoto.  Dopo la connessione, se non è aperto il progetto corretto, al momento dell'interruzione dell'applicazione verrà visualizzata una finestra di dialogo.  In questa finestra di dialogo è necessario immettere il percorso dei file di origine dell'applicazione.  Il nome file specificato nella finestra di dialogo deve corrispondere a quello specificato nei simboli di debug, che si trovano sul server Web.  Per ulteriori informazioni, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Procedura: attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Procedura: individuare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)