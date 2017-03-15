---
title: "Errore: impossibile avviare il debug sul server Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.http"
  - "vwd.nonadmin.error."
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, errori dell'applicazione Web"
  - "debug [Visual Studio], errori"
  - "debug di applicazioni Web ASP.NET, impossibile avviare il debug dell'errore"
  - "errori [debugger], impossibile avviare il debug"
  - "HTTP (server), debug dell'errore"
  - "IIS, debug di DLL"
  - "debug remoto, errori"
  - "sicurezza [debugger], applicazioni Web"
  - "impostazioni di sicurezza, controllo di siti Web predefiniti"
  - "impossibile avviare il debug dell'errore"
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 31
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: impossibile avviare il debug sul server Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si prova a eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, potrebbe essere visualizzato questo messaggio di errore: Impossibile avviare il debug sul server Web.  
  
 Nella maggior parte dei casi questo errore si verifica perché IIS non è configurato correttamente.  
  
##  <a name="vxtbshttpservererrorsthingstocheck"></a> Verificare che IIS sia configurato correttamente  
 Per informazioni sulla distribuzione di IIS 8 con un'app MVC 5, vedere l'articolo sulla [pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
 Per informazioni sulla distribuzione in IIS 7.5, vedere [Debug remoto di ASP.NET in un computer remoto con IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).  
  
##  <a name="vxtbshttpservererrorswebapplicationsonremoteservers"></a> Verificare che Visual Studio Remote Tools sia installato  
 Se si sta provando a eseguire il debug in un server Web remoto, è necessario installare Visual Studio Remote Tools. Per informazioni sul download e la configurazione di Remote Tools, vedere [Debug remoto](../debugger/remote-debugging.md).  
  
##  <a name="vxtbshttpservererrorsanchor2"></a> Verificare che ASP.NET sia installato  
 **IIS 8**  
  
 Per IIS 8, ASP.NET è installato come parte di IIS.  
  
1.  Nel riquadro **Server Manager** selezionare **Dashboard**, quindi fare clic su **Aggiungi ruoli e funzionalità**.  
  
2.  Nella pagina **Tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**, quindi fare clic su **Avanti**.  
  
3.  Nella pagina **Selezione server di destinazione** scegliere **Selezionare un server dal pool di server**, quindi selezionare il server e fare clic su **Avanti**.  
  
4.  Nella pagina **Selezione ruoli server** selezionare **Server Web \(IIS\)** e fare clic su **Avanti**.  
  
5.  Nella pagina **Selezione funzionalità** fare clic su **Avanti**.  
  
6.  Nella pagina **Ruolo Server Web \(IIS\)** fare clic su **Avanti**.  
  
7.  Nella pagina **Selezione servizi ruolo** prendere nota dei servizi ruolo preselezionati installati per impostazione predefinita, espandere il nodo **Server applicazioni** e il nodo **.NET Framework 4.5**, quindi selezionare **ASP.NET 4.5**. Se è stato installato .NET 3.5, selezionare anche **ASP.NET 3.5**.  
  
8.  Nella pagina **Conferma selezioni per l'installazione** fare clic su **Installa**.  
  
9. Nella pagina **Stato dell'installazione** verificare che l'installazione del ruolo Server Web \(IIS\) e dei servizi ruolo necessari sia stata completata correttamente, quindi fare clic su **Chiudi**.  
  
 **IIS 7.5 e versioni precedenti**  
  
 Per IIS 7.5 e versioni precedenti: da una finestra del prompt dei comandi eseguire il comando seguente:  
  
```  
systemroot\Microsoft.NET\Framework\ versionNumber \aspnet_regiis -i   
```  
  
## Risoluzione dei problemi di base  
 Ecco alcune operazioni da eseguire per assicurarsi che l'applicazione ASP.NET sia distribuita correttamente.  
  
## Visualizzare la pagina localhost nel browser  
 Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.  
  
## Visualizzare la pagina Web nel browser  
 Avviare un Web browser e digitare l'URL della pagina di cui si sta provando a eseguire il debug \(ad esempio: `http://localhost/MyWebApplication`\). Se IIS non è configurato correttamente o l'applicazione ASP.NET non è stata distribuita correttamente, dovrebbero essere visualizzati degli errori che consentono di risolvere i problemi di installazione di IIS e di distribuzione di ASP.NET.  
  
## Creare un'applicazione ASP.NET di base nel server  
 Provare a creare un'applicazione ASP.NET di base in locale nel server e a eseguirne il debug.  
  
## Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP  
 Il debug di un server Web richiede l'autenticazione NTLM. Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Per risolvere questo problema, è possibile specificare il nome del computer remoto.  
  
##  <a name="vxtbshttpservererrorsmanuallyattaching"></a> Connessione manuale al processo  
 Se viene visualizzato ancora un messaggio di errore all'avvio del debug, provare a eseguire il debug dell'applicazione collegandola manualmente al processo.  
  
-   Avviare l'applicazione senza eseguire il debug, scegliendo **Avvia senza eseguire debug** dal menu **Debug**.  
  
-   Fare clic su **Debug\/Connetti a processo**.  Quando viene visualizzata la finestra, abilitare **Mostra i processi di tutti gli utenti**.  
  
-   Individuare il processo appropriato e collegarlo. Per le app di ASP.NET precedenti a MVC 5, il processo è w3wp.exe. Per MVC 5, vedere l'articolo sulla [pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html).  
  
## Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)