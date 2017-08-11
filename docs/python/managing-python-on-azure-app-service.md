---
title: Gestione di Python nel servizio app di Azure | Microsoft Docs
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 5b509a46dd3dbee3a45ab2eac57242636beee17b
ms.contentlocale: it-it
ms.lasthandoff: 07/18/2017

---

# <a name="managing-python-on-azure-app-service"></a>Gestione di Python nel servizio app di Azure

Il [servizio app di Azure](https://azure.microsoft.com/services/app-service/) è un'offerta di tipo piattaforma distribuita come servizio per le app Web, siano esse siti accessibili tramite un browser, API REST usate dai client o elaborazioni attivate da eventi. Il servizio app supporta pienamente l'uso di Python per implementare le app.

Il supporto di Python nel servizio app di Azure viene offerto come un set di estensioni del sito del servizio app, ognuna contenente una versione specifica del runtime di Python. È consigliabile la versione più recente di Python 3, ovviamente, ma se necessario si può scegliere una versione precedente. In questo argomento viene illustrato come installare e configurare un'estensione del sito insieme a tutti i pacchetti desiderati.

> [!Note]
> Le procedure descritte di seguito sono soggette a modifiche, in particolare per apportare miglioramenti. Le modifiche sono annunciate nel [blog Python Engineering at Microsoft](https://blogs.msdn.microsoft.com/pythonengineering/) (Progettazione Python in Microsoft).

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Scelta di una versione di Python tramite il portale di Azure

Se il sito è già distribuito e in esecuzione nel servizio app di Azure, passare al pannello Servizio App, scorrere verso la sezione **Strumenti di sviluppo** e quindi selezionare **Estensioni > Aggiungi**. Scorrere l'elenco per individuare le estensioni specifiche per la versione di Python desiderata. L'elenco presenta l'inconveniente di non essere ordinabile, pertanto le diverse versioni sono spesso sparse nell'elenco:

![Portale di Azure con estensioni di Python](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Scelta di una versione di Python tramite Azure Resource Manager

Se si distribuisce il sito con un modello di Azure Resource Manager, aggiungere l'estensione del sito come risorsa. L'estensione viene visualizzata come una risorsa annidata del sito con il tipo `siteextensions` e il nome da [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22).

Ad esempio, dopo l'aggiunta di un riferimento a `python361x64` (Python 3.6.1 x64), il modello potrebbe essere simile al seguente:

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
      "resources": [
        {
          "apiVersion": "2015-08-01",
          "name": "python361x64",
          "type": "siteextensions",
          "properties": { },
          "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
          ]
        },
      ...
```

## <a name="configuring-your-site"></a>Configurazione del sito

Dopo aver installato l'estensione del sito (tramite il portale o un modello di Azure Resource Manager), il percorso di installazione di Python sarà simile a `d:\home\python361x64\python.exe`. Per visualizzare il percorso specifico, selezionare l'estensione nell'elenco visualizzato per il servizio app per aprire la pagina di descrizione contenente il percorso:

![Elenco delle estensioni nel servizio app di Azure](media/python-on-azure-extension-list.png)

![Dettagli delle estensioni nel servizio app di Azure](media/python-on-azure-extension-detail.png)

Il passaggio successivo consiste nel fare riferimento all'installazione di Python nel file `web.config` del sito per i gestori di richieste FastCGI e HTTP Platform.

### <a name="using-the-fastcgi-handler"></a>Uso del gestore FastCGI

FastCGI è un'interfaccia che funziona a livello di richiesta. IIS riceve le connessioni in ingresso e inoltra ogni richiesta a un'app WSGI in esecuzione in uno o più processi Python persistenti. Il [pacchetto wfastcgi](https://pypi.io/project/wfastcgi) è pre-installato e configurato con ogni estensione del sito Python, pertanto è possibile abilitarlo facilmente includendo il codice seguente in `web.config`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Le `<appSettings>` sono disponibili come variabili di ambiente per l'app:
- Il valore per `PYTHONPATH` può essere esteso liberamente, ma deve includere la directory radice del sito.
- `WSGI_HANDLER` deve puntare a un'app WSGI importabile dal sito.
- `WSGI_LOG` è facoltativo ma consigliato per il debug del sito. 

In `<handlers>`, verificare che l'attributo `scriptProcessor` e l'elemento `<add>` contengano i percorsi corretti per l'installazione specifica. Il percorso viene nuovamente visualizzato nel pannello dei dettagli dell'estensione.

### <a name="using-the-http-platform-handler"></a>Uso del gestore HTTP Platform

Il modulo HTTP Platform passa le connessioni socket direttamente a un processo di Python autonomo. Questo pass-through consente di eseguire qualsiasi server Web, ma richiede uno script di avvio che esegue un server Web locale. Specificare lo script nell'elemento `<httpPlatform>`, dove l'attributo `processPath` punta a Python e l'attributo `arguments` punta allo script e a eventuali argomenti che si vogliono specificare:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Il percorso a `python.exe` nella configurazione è, naturalmente, specifico per la versione installata.

La variabile di ambiente `HTTP_PLATFORM_PORT` illustrata nel codice contiene la porta sulla quale il server locale deve essere in ascolto per le connessioni da localhost. In questo esempio viene anche illustrato come creare un'altra eventuale variabile di ambiente, in questo caso `SERVER_PORT`.

## <a name="installing-packages"></a>Installazione di pacchetti

Poiché è probabile che l'app dipenda da una serie di pacchetti, è necessario verificare che tali pacchetti siano installati nell'ambiente Python in uso nel servizio app con uno dei tre metodi seguenti:

- La console del servizio app di Azure nel portale di Azure
- L'API REST Kudu
- La copia di ogni libreria nel codice sorgente dell'app

### <a name="kudu-console"></a>Console Kudu

La [console Kudu](https://github.com/projectkudu/kudu/wiki/Kudu-console) offre l'accesso diretto da riga di comando con privilegi elevati al server del servizio app e al relativo file system. Oltre a essere un utile strumento di debug, può anche essere usata per le configurazioni basate su CLI.

Accedere a Kudu dal pannello Servizio app selezionando **Strumenti di sviluppo > Strumenti avanzati** e quindi **Vai** per passare a un URL che è uguale all'URL del servizio app di base tranne che per l'inserimento di `.scm`. Ad esempio, se l'URL di base è `https://vspython-test.azurewebsites.net/` Kudu è su `https://vspython-test.scm.azurewebsites.net/`:

![Console Kudu per il servizio app di Azure](media/python-on-azure-console01.png)

Selezionare **Console di debug > CMD** per aprire la console, in cui è possibile esplorare l'installazione di Python e vedere quali librerie sono già presenti.

Per installare un singolo pacchetto:

1. Passare alla cartella di installazione di Python in cui si vuole installare il pacchetto, ad esempio `d:\home\python361x64`.
1. Usare `python.exe -m pip install <package_name>` per installare un pacchetto.

![Esempio di installazione di matplotlib tramite la console Kudu per il servizio app di Azure](media/python-on-azure-console02.png)

Per installare i pacchetti da `requirements.txt` (scelta consigliata):

1. Passare alla cartella di installazione di Python in cui si vuole installare il pacchetto, ad esempio `d:\home\python361x64`.
1. Usare `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` per installare un pacchetto.

È consigliabile usare requirements.txt perché è facile riprodurre l'esatto set di pacchetti sia in locale che nel server.

> [!Note]
> Non è presente alcun compilatore C nel server Web, pertanto è necessario installare il file wheel per tutti i pacchetti con moduli di estensione nativa. Molti pacchetti diffusi offrono i propri file wheel. Per i pacchetti che non li offrono, usare `pip wheel <package_name>` nel computer di sviluppo locale e quindi caricare il file wheel nel proprio sito. Per un esempio, vedere [Gestione dei pacchetti necessari](python-environments.md#managing-required-packages)

### <a name="kudu-rest-api"></a>API REST Kudu

Anziché usare la console Kudu tramite il portale di Azure, è possibile eseguire comandi in modalità remota tramite l'API REST Kudu inserendo il comando su `https://yoursite.scm.azurewebsites.net/api/command`. Ad esempio, per installare il pacchetto `matplotlib`, inserire il JSON seguente su `/api/command`:

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

Per informazioni sui comandi e l'autenticazione, vedere la [documentazione di Kudu](https://github.com/projectkudu/kudu/wiki/REST-API). È anche possibile visualizzare le credenziali usando [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) dall'interfaccia della riga di comando di Azure. Una libreria helper per l'inserimento dei comandi Kudu è disponibile anche su GitHub (https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).


### <a name="copying-libraries-into-app-source-code"></a>Copia delle librerie nel codice sorgente dell'app

Anziché installare i pacchetti direttamente sul server, è possibile copiare le librerie nel codice sorgente e distribuirle come se facessero parte dell'app. A seconda di quante dipendenze sono presenti e della loro frequenza di aggiornamento, questo metodo può essere il modo più semplice per ottenere una distribuzione funzionante.

Il problema è che queste librerie devono corrispondere esattamente alla versione di Python nel server, in caso contrario verranno visualizzati errori sconosciuti dopo la distribuzione. Tuttavia, poiché le versioni di Python nelle estensioni del sito del servizio app sono esattamente le stesse rilasciate su python.org, è possibile ottenere facilmente una versione compatibile per la distribuzione locale.

### <a name="avoiding-virtual-environments"></a>Come evitare gli ambienti virtuali

Anche se lavorare in un ambiente virtuale in locale può essere utile per comprendere pienamente le dipendenze richieste dal sito, l'uso degli ambienti virtuali nel servizio app non è consigliato. Limitarsi invece a installare le librerie nella cartella principale di Python e distribuirle con l'app in modo da evitare dipendenze in conflitto.
