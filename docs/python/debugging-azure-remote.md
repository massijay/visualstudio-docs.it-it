---
title: Debug remoto in Azure con Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68fdc53-65a1-423c-8964-9815dbb3387e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d2caa21359655a2079a853123baea31e471ba040
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---

# <a name="remotely-debugging-python-code-on-azure"></a>Debug remoto di codice Python in Azure

Il [supporto per Python in Visual Studio](installation.md) include la possibilità di eseguire il debug in remoto del codice Python in esecuzione in Servizio app di Azure. Diversamente dal semplice debug remoto, il computer di destinazione in questo scenario non è accessibile direttamente tramite TCP, quindi Visual Studio fornisce un proxy che espone il protocollo del debugger tramite HTTP. I progetti creati con il modello Web configurano automaticamente questo proxy nel file `web.debug.config` generato. Il debug remoto viene abilitato anche quando si pubblica una configurazione per il debug del progetto, come descritto in [Publishing to Azure App Service](template-web.md#publishing-to-azure-app-service) (Pubblicazione in Servizio app di Azure).

Dato che il debug remoto di Azure usa WebSocket, è necessario abilitare i socket per il servizio app tramite il [portale di Azure](https://portal.azure.com). Passare a **Impostazioni > Impostazioni applicazione** e impostare **Impostazioni generali > Web Socket** su **Attivato**, quindi selezionare **Salva** per applicare la modifica. (Si noti che le impostazioni **Debug** non sono valide per il debug di Python.)

![Abilitazione di WebSocket nel portale di Azure](~/docs/python/media/azure-remote-debugging-enable-web-sockets.png)

Dopo aver distribuito correttamente il progetto e aver abilitato WebSocket, è possibile collegarsi al servizio app da **Esplora server** in Visual Studio (**Visualizza > Esplora server**). Individuare il sito in **Azure > Servizio app** e il gruppo di risorse applicabile, fare clic con il pulsante destro del mouse e scegliere **Collega debugger (Python)**. (Si noti che il comando **Collega debugger** è per le applicazioni .NET in esecuzione in IIS e risulta utile solo se si ospita codice .NET insieme all'app Python.)

Visual Studio potrebbe indirizzare a un set di istruzioni per il collegamento diretto, come descritto di seguito in [Collegamento senza Esplora server](#attaching-without-server-explorer). Se non viene visualizzato il comando **Collega debugger (Python)** o Visual Studio non riesce a collegarsi al sito, vedere [Risoluzione dei problemi di debug remoto in Azure](debugging-azure-remote-troubleshooting.md).

Se il collegamento riesce, Visual Studio passa a una visualizzazione del debugger. La barra degli strumenti dovrebbe indicare il processo in corso di debug come URI `wss://`:

![Debug di un sito Web di Servizio app di Azure](~/docs/python/media/azure-remote-debugging-attached.png)

Dopo aver attivato il collegamento, l'esperienza di debug è fondamentalmente uguale al normale debug remoto, con alcune restrizioni. In particolare, il server Web IIS che gestisce le richieste in ingresso e le delega al codice Python attraverso FastCGI ha un timeout per la gestione delle richieste, pari a 90 secondi per impostazione predefinita. Se la gestione della richiesta richiede più tempo (ad esempio perché il processo viene sospeso in un punto di interruzione), IIS terminerà il processo con conseguente interruzione immediata della sessione di debug. 

## <a name="attaching-without-server-explorer"></a>Collegamento senza Esplora server

Per collegare il debugger direttamente al servizio app, seguire le istruzioni fornite nella pagina di informazioni sul proxy WebSocket che Visual Studio distribuisce nel sito all'indirizzo `<site_url>/ptvsd`, ad esempio `ptvsdemo.azurewebsites.net/ptvsd`. Quando si visita questa pagina viene anche eseguita una verifica della corretta configurazione del proxy:

![Pagina di informazioni sul proxy per il debug remoto in Azure](~/docs/python/media/azure-remote-debugging-proxy-info-page.png)

Come indicato, sarà necessario costruire un URL usando il segreto da `web.debug.config`, che viene rigenerato a ogni pubblicazione del progetto. Questo file è nascosto per impostazione predefinita in Esplora soluzioni e non è incluso nel progetto, pertanto sarà necessario visualizzare tutti i file oppure aprirlo in un editor separato. Dopo aver aperto il file, prendere nota del valore dell'appSetting denominata `WSGI_PTVSD_SECRET`:

![Determinazione dell'endpoint del debugger in Servizio app di Azure](~/docs/python/media/azure-remote-debugging-secret.png)

L'URL ora necessario è nel formato `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` dove &lt;secret&gt; e &lt;site_name&gt; nella stringa devono essere ovviamente sostituiti con i valori specifici.

Per collegare il debugger, selezionare **Debug > Connetti a processo**, selezionare **Debug remoto Python** nell'elenco a discesa **Trasporto**, immettere l'URL nella casella di testo **Qualificatore** e premere INVIO. Se Visual Studio riesce a connettersi correttamente al servizio app, viene visualizzato un singolo processo Python nell'elenco. Selezionarlo e quindi selezionare **Associa** per avviare il debug:

![Uso della finestra di dialogo Connetti a processo per collegarsi a un sito Web di Azure](~/docs/python/media/azure-remote-debugging-manual-attach.png)

