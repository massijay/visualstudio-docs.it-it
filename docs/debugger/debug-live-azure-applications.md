---
title: Debug in tempo reale delle app di Azure ASP.NET - Visual Studio | Documenti Microsoft
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02f91441c493d65e8abcdc80bd85b01f2bd423bf
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2017
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debug in tempo reale delle app di Azure ASP.NET utilizzando il Debugger di Snapshot

Quando viene eseguito codice che si è interessati, il Debugger di Snapshot crea uno snapshot delle applicazioni in produzione. Per indicare al debugger di eseguire uno snapshot, impostare snappoints e logpoints nel codice. Il debugger consente di vedere esattamente cosa non ha funzionato, senza alcun impatto sul traffico dell'applicazione di produzione. Il Debugger Snapshot consentono di ridurre notevolmente il tempo che necessario per risolvere i problemi che si verificano negli ambienti di produzione.

Snappoints e logpoints sono simili ai punti di interruzione. A differenza dei punti di interruzione, snappoints non arrestano l'applicazione quando raggiunto. In genere, l'acquisizione dello snapshot in un snappoint accetta 10-20 millisecondi. 

Raccolta di snapshot è disponibile per le seguenti App web in esecuzione in Azure App Service:

- Le applicazioni ASP.NET in esecuzione in .NET Framework 4.6.1 o versioni successive.
- Applicazioni ASP.NET Core in esecuzione su .NET Core 2.0 o versione successiva in Windows.

Inoltre, il Debugger dello Snapshot è disponibile solo per Visual Studio 2017 Enterprise 15,5 o versione successiva e piani di servizio App di base o versione successiva. 

## <a name="start-the-snapshot-debugger"></a>Avviare il Debugger di Snapshot

1. Installare il [Visual Studio Enterprise 15,5 Preview](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-preview-relnotes) o versione successiva. Se si sta aggiornando un'anteprima di Visual Studio 2017 precedente, eseguire il programma di installazione Visual Studio e controllare il componente del Debugger di Snapshot del carico di lavoro di sviluppo ASP.NET e web.

2. Aprire il progetto che si desidera eseguire il debug di snapshot. 

    > [!IMPORTANT] 
    > Eseguire il debug di snapshot, è necessario aprire il **stessa versione del codice sorgente** che viene pubblicato il servizio App di Azure. 

3. In Esplora risorse Cloud (selezionare **Vista > Cloud Explorer**), fare clic con il pulsante destro viene distribuito il progetto per il servizio App di Azure e selezionare **collega Debugger Snapshot** per avviare il Debugger di Snapshot.

   ![Avviare il debugger snapshot](../debugger/media/snapshot-launch.png "avviare il debugger di snapshot")

    La prima volta che si seleziona **collega Debugger Snapshot**, viene chiesto di installare il Debugger di Snapshot del servizio App di Azure. Questa installazione richiede un riavvio del servizio App di Azure. 

   Visual Studio è in modalità di debug di snapshot.

   ![Modalità di debug snapshot](../debugger/media/snapshot-message.png "modalità di debug di Snapshot")

   Il **moduli** finestra viene visualizzato quando tutti i moduli sono caricati per il servizio App di Azure (scegliere **Debug / Windows / moduli** per aprire questa finestra).

   ![Controllare la finestra moduli](../debugger/media/snapshot-modules.png "controllare la finestra moduli")

## <a name="set-a-snappoint"></a>Impostare un snappoint

1. Nell'editor di codice, fare clic sulla barra di navigazione a sinistra accanto a una riga di codice che si desidera impostare un snappoint. Verificare che si tratta di codice che verrà eseguita.

   ![Impostare un snappoint](../debugger/media/snapshot-set-snappoint.png "impostare un snappoint")

2. Fare clic su **Start Collection** per attivare il snappoint.  

   ![Accendere il snappoint](../debugger/media/snapshot-start-collection.png "accendere il snappoint")

    > [!TIP]
    > Non è possibile eseguire durante la visualizzazione di uno snapshot, ma è possibile inserire più snappoints nel codice per seguire l'esecuzione in diverse righe di codice. Se si dispone di più snappoints nel codice, il Debugger dello Snapshot assicura che gli snapshot corrispondenti dalla stessa sessione dell'utente finale, anche se sono presenti più utenti raggiunge l'app.

## <a name="take-a-snapshot"></a>Creare uno snapshot

Quando viene attivata una snappoint, acquisisce uno snapshot ogni volta che viene eseguita la riga di codice in cui è posizionato il snappoint. L'esecuzione può essere causata da una richiesta effettiva sul server. Per forzare il snappoint da sottoporre a hit, è anche possibile passare alla visualizzazione esplorazione del sito web e intraprendere che le azioni necessarie che causano il snappoint da sottoporre a hit.

## <a name="inspect-snapshot-data"></a>Controllare i dati dello snapshot

1. Quando viene raggiunto il snappoint, nella finestra Strumenti di diagnostica viene visualizzato uno snapshot. Scegliere **Debug / Windows / Mostra strumenti di diagnostica** per aprire questa finestra.

   ![Aprire un snappoint](../debugger/media/snapshot-diagsession-window.png "aprire un snappoint")

1. Fare doppio clic per aprire lo snapshot nell'editor di codice il snappoint.

   ![Controllare i dati dello snapshot](../debugger/media/snapshot-inspect-data.png "controllare i dati dello snapshot")

   In questa vista è possibile passare il mouse sulle variabili per visualizzare i suggerimenti dati, utilizzare il **variabili locali**, **controlla**, e **Stack di chiamate** windows e anche valutare le espressioni.

    Il sito Web è ancora in tempo reale e gli utenti finali non sono stati interessati. Un solo snapshot viene acquisito per snappoint per impostazione predefinita: dopo aver acquisito uno snapshot di snappoint viene disattivata. Se si desidera acquisire snapshot di un altro nel snappoint, è possibile attivare il snappoint indietro facendo **Aggiorna insieme**.

È anche possibile aggiungere ulteriori snappoints all'app e attivarli con il **Aggiorna insieme** pulsante.

**Serve aiuto?** Vedere il [problemi noti e risoluzione dei problemi](../debugger/debug-live-azure-apps-troubleshooting.md) e [domande frequenti relative al debug snapshot](../debugger/debug-live-azure-apps-faq.md) pagine.

## <a name="set-a-conditional-snappoint"></a>Impostare un snappoint condizionale

Se è difficile ricreare un determinato stato nell'app, è consigliabile se si consente l'utilizzo di un snappoint condizionale. È possibile utilizzare snappoints condizionale per evitare di creare uno snapshot fino a quando l'app passa allo stato desiderato, ad esempio quando una variabile ha un valore specifico si è interessati. È possibile impostare le condizioni di utilizzo di espressioni, filtri, o conteggio.

#### <a name="to-create-a-conditional-snappoint"></a>Per creare un snappoint condizionale

1. Fare doppio clic su un'icona di snappoint (la palla vuota) e scegliere **impostazioni**.

   ![Scegliere impostazioni](../debugger/media/snapshot-snappoint-settings.png "scegliere impostazioni")

1. Nella finestra Impostazioni snappoint, digitare un'espressione.

   ![Digitare un'espressione](../debugger/media/snapshot-snappoint-conditions.png "digitare un'espressione")

   Nell'illustrazione precedente, viene creato lo snapshot solo per il snappoint quando `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Impostare un logpoint

Oltre a creare uno snapshot quando viene raggiunto un snappoint, è inoltre possibile configurare un snappoint per registrare un messaggio (ossia, creare un logpoint). È possibile impostare logpoints senza dover ridistribuire l'applicazione. Logpoints vengono eseguiti quasi e non causare alcun impatto o effetti collaterali all'applicazione in esecuzione.

#### <a name="to-create-a-logpoint"></a>Per creare un logpoint

1. Fare doppio clic su un'icona di snappoint (esagono blu) e scegliere **impostazioni**.

1. Nella finestra Impostazioni snappoint selezionare **azioni**.

    ![Creare un logpoint](../debugger/media/snapshot-logpoint.png "creare un logpoint")

1. Nel campo messaggio, è possibile immettere il nuovo messaggio di log che si desidera registrare. È inoltre possibile valutare le variabili nel messaggio di log, inserirli all'interno delle parentesi graffe.

    Se si sceglie **inviare alla finestra di Output**, quando viene raggiunto il logpoint, viene visualizzato il messaggio nella finestra Strumenti di diagnostica.

    ![Per i dati nella finestra diagsession Logpoint](../debugger/media/snapshot-logpoint-output.png "Logpoint i dati nella finestra diagsession")

    Se si sceglie **invia al registro applicazioni**, quando viene raggiunto il logpoint, il messaggio viene visualizzato in qualsiasi punto che è possibile visualizzare i messaggi da `System.Diagnostics.Trace` (o `ILogger` in .NET Core), ad esempio [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Passaggi successivi

- Per informazioni su come controllare le variabili durante la visualizzazione di uno snapshot, vedere [Debbuger funzionalità presentazione](../debugger/debugger-feature-tour.md).
- Visualizzazione di [domande frequenti relative al debug snapshot](../debugger/debug-live-azure-apps-faq.md).
- Visualizzazione [risoluzione dei problemi noti per il debug di snapshot e suggerimenti](../debugger/debug-live-azure-apps-troubleshooting.md).
- Se si desidera visualizzare gli snapshot in Application Insights quando l'applicazione raggiunge un'eccezione, è possibile farlo. Per ulteriori informazioni, vedere [Debug snapshot in caso di eccezioni nelle applicazioni .NET](/azure/application-insights/app-insights-snapshot-debugger). Application Insights supporta le applicazioni di Service Fabric oltre a servizio App di Azure.
