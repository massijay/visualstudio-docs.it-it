---
title: 'Errore: Impossibile avviare il debug sul Server Web | Documenti Microsoft'
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5332933bf1452ca730b5c49716e10f49851fd749
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Errore: impossibile avviare il debug sul server Web

Quando si tenta di eseguire il debug di un'applicazione ASP.NET in esecuzione in un server Web, potrebbe essere visualizzato questo messaggio di errore: `Unable to start debugging on the Web server`.

Questo errore si verifica spesso, perché una modifica della configurazione o di errore si è verificato che richiede un aggiornamento per il pool di applicazioni, reimpostazione di IIS o entrambi. È possibile reimpostare IIS, aprire un prompt dei comandi con privilegi elevati e digitare `iisreset`. 

## <a name="specificerrors"></a>Che cos'è il messaggio di errore dettagliato?

Il `Unable to start debugging on the Web server` messaggio è di tipo generico. In genere, un messaggio più specifico è incluso nella stringa di errore e che consentono di identificare la causa del problema o cercare una correzione più precisa. Ecco alcuni dei messaggi di errore più comuni che vengono aggiunti al messaggio di errore principale:

- [IIS non include un sito Web che corrisponde al lancio url](#IISlist)
- [Il server web non è configurato correttamente](#web_server_config)
- [Impossibile connettersi al server Web](#unabletoconnect)
- [Il server web non ha risposto nel tempo previsto](#webservertimeout)
- [Microsoft visual studio remota debugging monitor(msvsmon.exe) sembra non essere in esecuzione nel computer remoto](#msvsmon)
- [Il server remoto ha restituito un errore](#server_error)
- [Impossibile avviare il debug ASP.NET](#aspnet)
- [Il debugger non può connettersi al computer remoto](#cannot_connect)
- [Vedere la Guida per gli errori comuni di configurazione. Esegue la pagina Web all'esterno del debugger per ottenere ulteriori informazioni.](#see_help)

## <a name="IISlist"></a>IIS non include un sito Web che corrisponde al lancio url

- Riavviare Visual Studio come amministratore, quindi ripetere il debug. (Alcuni scenari di debug di ASP.NET richiedono privilegi elevati).

    È possibile configurare Visual Studio per eseguire sempre come amministratore facendo clic sull'icona di scelta rapida di Visual Studio, scegliere **proprietà > Avanzate**e scegliendo quindi di eseguire sempre come amministratore.

## <a name="web_server_config"></a>Il server web non è configurato correttamente

- Vedere [errore: il server web non è configurato correttamente](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a>Impossibile connettersi al server Web

- Sono in esecuzione Visual Studio e il server Web nello stesso computer e il debug con **F5** (anziché **Connetti a processo**)? Aprire le proprietà del progetto e verificare che il progetto è configurato per la connessione al server Web corretto e avviare l'URL. (Aprire **proprietà > Web > server** o **proprietà > Debug** a seconda del tipo di progetto. Per un progetto di Web Form, aprire **pagine delle proprietà > Opzioni di avvio > Server**.)

- In caso contrario, riavviare il Pool di applicazioni e quindi reimpostare IIS. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a>Il server web non ha risposto nel tempo previsto

- Reimpostare IIS, quindi ripetere il debug. Più istanze del debugger possono essere collegate al processo IIS. una reimpostazione termina in. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a>Microsoft visual studio remota debugging monitor(msvsmon.exe) sembra non essere in esecuzione nel computer remoto

- Se si esegue il debug in un computer remoto, assicurarsi di avere [installato ed eseguono il debugger remoto](../debugger/remote-debugging.md). Se il messaggio indica un firewall, assicurarsi che il [correggere le porte del firewall](../debugger/remote-debugger-port-assignments.md) aperte, soprattutto se si utilizza un firewall di terze parti.
- Se si utilizza un file host, assicurarsi che sia configurato correttamente. Ad esempio, se il debug tramite **F5** (anziché **Connetti a processo**), gli host del file deve includere lo stesso URL di progetto come proprietà del progetto **proprietà > Web > server**  o **proprietà > Debug**, a seconda del tipo di progetto.

## <a name="server_error"></a>Il server remoto ha restituito un errore

Controllare il codice di errore che viene restituito nel messaggio per identificare la causa del problema. Ecco alcuni codici di errore comuni.
- (403) accesso negato. Verificare che ci si connette per il tipo di server e l'URL (in **proprietà > Web > server** o **proprietà > Debug**, a seconda del tipo di progetto). Inoltre, verificare che i file Web. config del server include `debug=true` nell'elemento di compilazione. Se queste impostazioni sono già corrette, verificare che la cartella dell'applicazione Web disponga delle autorizzazioni di cartella corretta. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).
- Server non disponibile (503). Il Pool di applicazioni potrebbe aver arrestato a causa di una modifica della configurazione o di errore. Riavviare il Pool di applicazioni.
- (404) non trovato. Assicurarsi che il Pool di applicazioni è configurato per la versione corretta di ASP.NET.

## <a name="aspnet"></a>Impossibile avviare il debug ASP.NET

- Riavviare il Pool di applicazioni e reimpostare IIS. Per ulteriori informazioni, vedere [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).
- Se si sta eseguendo la riscrittura URL, test Web. config base con alcun URL di riscrivere più volte. Vedere il **nota** sull'URL riscrivere modulo [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a>Il debugger non può connettersi al computer remoto

Se si esegue il debug in locale, questo errore può verificarsi perché Visual Studio è un'applicazione a 32 bit, pertanto utilizza la versione a 64 bit del debugger remoto per eseguire il debug di applicazioni a 64 bit. Aprire le proprietà del progetto e verificare che il progetto è configurato per connettere il server Web e l'URL corretto. (Aprire **proprietà > Web > server** o **proprietà > Debug** a seconda del tipo di progetto.)

Inoltre, se si utilizza un file host, verificare che sia configurato correttamente. Ad esempio, gli host nel file deve includere lo stesso URL di progetto come proprietà del progetto **proprietà > Web > server** o **proprietà > Debug**, a seconda del tipo di progetto.

## <a name="see_help"></a>Vedere la Guida per gli errori comuni di configurazione. Esegue la pagina Web all'esterno del debugger per ottenere ulteriori informazioni.

- Viene eseguito Visual Studio e il server Web nello stesso computer? Aprire le proprietà del progetto e verificare che il progetto è configurato per la connessione al server Web corretto e avviare l'URL. (Aprire **proprietà > Web > server** o **proprietà > Debug** a seconda del tipo di progetto.)

- Se il problema persiste o si esegue il debug in modalità remota, seguire i passaggi in [controllare la configurazione di IIS](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a>Controllare la configurazione di IIS

Dopo avere eseguito i passaggi descritti in questa sezione per risolvere il problema e prima di tentare nuovamente di eseguire il debug, è inoltre necessario reimpostare IIS. È possibile farlo aprendo un prompt dei comandi con privilegi elevati e digitando `iisreset`. 

* Arrestare e riavviare il pool di applicazioni IIS, quindi riprovare. 

    Il Pool di applicazioni potrebbe aver arrestato a causa di un errore. In alternativa, potrebbe richiedere un'altra modifica della configurazione apportate arrestare e riavviare il Pool di applicazioni.
    
    > [!NOTE]
    > Se il Pool di applicazioni continua ad arrestarsi, devi disinstallare URL Rewrite Module dal Pannello di controllo. È possibile reinstallarlo utilizzando l'installazione guidata piattaforma Web (WebPI). Questo problema può verificarsi dopo un aggiornamento di sistema significative.

* Controllare la configurazione del Pool di applicazioni, correggere l'errore, se necessario e quindi riprovare.

    Il Pool di applicazioni può essere configurato per una versione di ASP.NET che non corrisponde a progetto di Visual Studio. Aggiornare la versione ASP.NET nel Pool di applicazioni e riavviarlo. Per informazioni dettagliate, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Inoltre, se le credenziali di password sono stati modificati, potrebbe essere necessario aggiornarli nel Pool di applicazioni o nel sito Web.  Nel Pool di applicazioni, aggiornare le credenziali in **impostazioni avanzate > modello di processo > identità**. Per il sito Web, aggiornare le credenziali in **impostazioni di base > Connetti come...** . Riavviare il Pool di applicazioni.
    
* Controllare che la cartella dell'applicazione Web abbia le autorizzazioni appropriate.

    Assicurarsi di fornire IIS_IUSRS, IUSR o utente specifico associato la lettura di Pool di applicazioni e i diritti per la cartella dell'applicazione Web di esecuzione. Risolvere il problema e riavviare il Pool di applicazioni.

* Assicurarsi che sia installata la versione corretta di ASP.NET in IIS.

    Le versioni non corrispondenti di ASP.NET in IIS e nel progetto di Visual Studio possono causare questo problema. Si potrebbe essere necessario impostare la versione del framework in Web. config. Per installare ASP.NET in IIS, usare il [installazione guidata piattaforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vedere anche [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oppure, per ASP.NET Core, [Host su Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Risolvere gli errori di autenticazione se si usa solo l'indirizzo IP

     Per impostazione predefinita, gli indirizzi IP vengono considerati indirizzi Internet e l'autenticazione NTLM non viene eseguita su Internet. Se il sito web è configurato in IIS per richiedere l'autenticazione, l'autenticazione ha esito negativo. Per risolvere il problema, è possibile specificare il nome del computer remoto anziché l'indirizzo IP.
     
## <a name="other-causes"></a>Altre cause

Se la configurazione di IIS non causa il problema, provare questi passaggi:

- Riavviare Visual Studio con privilegi di amministratore e riprovare.

    Alcuni scenari di debug di ASP.NET, ad esempio tramite distribuzione Web richiedono privilegi elevati per Visual Studio.
    
- Se si eseguono più istanze di Visual Studio, riaprire il progetto in un'istanza di Visual Studio (con privilegi di amministratore) e riprovare.

- Se si utilizza un file HOSTS con gli indirizzi locali, provare a usare l'indirizzo di loopback anziché l'indirizzo IP del computer.

    Se non si utilizza gli indirizzi locali, assicurarsi che il file HOSTS include lo stesso URL di progetto come proprietà del progetto **proprietà > Web > server** o **proprietà > Debug**, a seconda del tipo di progetto.

## <a name="more-troubleshooting-steps"></a>Altre procedure di risoluzione dei problemi

* Visualizzare la pagina localhost nel browser sul server.

     Se IIS non è installato correttamente, dovrebbero essere visualizzati degli errori quando si digita `http://localhost` in un browser.
     
     Per ulteriori informazioni sulla distribuzione in IIS, vedere [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) e, per ASP.NET Core, [Host su Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Creare un'applicazione ASP.NET di base sul server oppure utilizzare un file Web. config di base.

    Se non è possibile ottenere l'app per funzionare con il debugger, provare a creare un'applicazione ASP.NET di base in locale nel server e provare a eseguire il debug di app di base. (Si potrebbe voler utilizzare il modello MVC ASP.NET predefinito). Se è possibile eseguire il debug di un'applicazione di base, che può identificare le differenze tra le due configurazioni. Cercare le differenze nelle impostazioni nel file Web. config, ad esempio le regole di riscrittura dell'URL.

## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)