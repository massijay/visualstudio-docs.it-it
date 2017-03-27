---
title: Debug remoto multipiattaforma con Python Tools for Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa667357-763f-4ce6-8e47-48f9337658a8
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
translationtype: Human Translation
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 7634da4bdc2b0186f410acb4eaf57a70ddea3e91
ms.lasthandoff: 03/10/2017

---

# <a name="remotely-debugging-python-code"></a>Debug remoto di codice Python

Python Tools for Visual Studio (PTVS) consente di avviare ed eseguire il debug di applicazioni Python in locale e in remoto in un computer Windows (vedere [Debug remoto](../debugger/remote-debugging.md)). È anche possibile eseguire il debug in remoto su un altro sistema operativo o dispositivo oppure su un'implementazione di Python diversa da CPython usando la [libreria ptvsd](https://pypi.python.org/pypi/ptvsd).

Quando si usa ptvsd, il codice Python di cui si esegue il debug ospita il server di debug a cui può collegarsi Visual Studio. Ciò richiede una piccola modifica del codice per importare e abilitare il server e potrebbe richiedere configurazioni della rete o del firewall nel computer remoto per consentire le connessioni TCP.

Per un'introduzione al debug remoto, vedere [Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (Approfondimento: il debug multipiattaforma) (youtube.com, 6m22s).

> [!VIDEO https://www.youtube.com/embed/y1Qq7BrV6Cc]

## <a name="preparing-the-script-for-debugging"></a>Preparazione dello script per il debug

1. Creare un file Python con il codice seguente nel computer remoto:

  ```python
  import random

  guesses_made = 0
  name = raw_input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print 'Well, {0}, I am thinking of a number between 1 and 20.'.format(name)

  while guesses_made < 6:
      guess = int(raw_input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print 'Your guess is too low.'
      if guess > number:
          print 'Your guess is too high.'
      if guess == number:
          break
  if guess == number:
      print 'Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made)
  else:
      print 'Nope. The number I was thinking of was {0}'.format(number)
  ```
 
1. Installare il pacchetto `ptvsd` nell'ambiente usando `pip install ptvsd`.

1. Abilitare il debug remoto aggiungendo il codice seguente nel primo punto possibile nello script, prima di altro codice. Anche se non è un requisito vincolante, non è possibile eseguire il debug di qualsiasi thread in background generato prima della chiamata della funzione `enable_attach`.

   ```python
   import ptvsd
   ptvsd.enable_attach(secret='my_secret')
   ```

   Il parametro `secret` passato a `enable_attach` viene usato per limitare l'accesso allo script in esecuzione. Al momento del collegamento sarà necessario specificarlo in Visual Studio o la connessione verrà negata. Per disabilitare questo scenario e consentire a chiunque la connessione, usare `enable_attach(secret=None)`.

1. Salvare il file e avviare lo script nel computer remoto. Si noti che la chiamata a `enable_attach` viene eseguita in background e attende connessioni in ingresso. Se richiesto, è possibile chiamare la funzione `wait_for_attach` dopo `enable_attach` per bloccare il programma fino al collegamento del debugger.

Oltre a `enable_attach` e `wait_for_attach`, ptvsd offre anche una funzione helper `break_into_debugger`, che funge da punto di interruzione programmatico se il debugger è collegato. È anche disponibile una funzione `is_attached` che restituisce `True` se il debugger è collegato (si noti che non è necessario verificare questo risultato prima di chiamare qualsiasi altra funzione `ptvsd`).

## <a name="attaching-remotely-from-python-tools"></a>Collegamento remoto da Python Tools

In questa procedura verrà impostato una semplice punto di interruzione per arrestare il processo remoto.

1. Creare una copia del file remoto nel computer locale e aprirlo in Visual Studio. La posizione del file non è importante, ma il relativo nome deve corrispondere al nome dello script nel computer remoto che verrà collegato.

1. Scegliere **Debug > Connetti a processo** per aprire la finestra di dialogo "Connetti a processo".

1. Impostare **Trasporto** su **Debug remoto Python**.

1. Immettere l'indirizzo del computer remoto nel campo **Qualificatore** e premere INVIO. Verranno elencati i processi disponibili in tale computer:

![Immissione del qualificatore ed elenco dei processi](media/remote-debugging-qualifier.png)

1. Un errore in questa fase indica in genere che il segreto non corrisponde, che la versione di `ptvsd` non corrisponde a quella usata da PTVS o che non è stato possibile stabilire una connessione. Una delle cause comuni di errori di connessione è la presenza di un firewall nel computer remoto che impedisce l'apertura della porta del server di debug (numero predefinito 5678). È possibile riconfigurare il firewall o usare una porta diversa. In quest'ultimo caso è necessario specificarla in modo esplicito nella chiamata a `enable_attach` nel parametro `address`, ad esempio:

  ```python
  ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))
  ```

  Il formato dell'indirizzo è lo stesso di quello usato dal socket del modulo Python standard per i socket di tipo `AF_INET`. Per informazioni dettagliate, vedere la [documentazione](http://docs.python.org/3/library/socket.html#socket-families) relativa. 

1. Quando il processo viene visualizzato nell'elenco, fare doppio clic su di esso per collegarsi. Visual Studio visualizza gli strumenti di debug mentre continua l'esecuzione dello script. Per lo script di esempio illustrato in precedenza, quando si immette un numero viene raggiunto il punto di interruzione:

    ![Punto di interruzione raggiunto](media/remote-debugging-breakpoint-hit.png)

1. A questo punto è possibile usare tutte le normali funzionalità di debug di PTVS. 

1. Quando si arresta il debug, Visual Studio si scollega dallo script, ma l'esecuzione dello script continuerà nel computer remoto. Anche l'esecuzione del server di debug continua nel thread in background corrispondente, quindi è possibile ricollegarsi al processo in un secondo momento usando la stessa procedura.


## <a name="securing-the-debugger-connection-with-ssl"></a>Protezione della connessione del debugger con SSL

Per impostazione predefinita, la connessione al server di debug remoto di PTVS non è protetta in alcun modo. Chiunque disponga del segreto può connettersi e tutti i dati vengono passati come testo normale. Di conseguenza, altri utenti nella rete possono intercettare i dati o anche eseguire un attacco man-in-the-middle (MITM). Per evitare questo problema durante il debug su reti non protette o su Internet, il server di debug supporta SSL. 

Per proteggere il canale con SSL, è necessario un certificato SSL. È possibile generare un certificato autofirmato manualmente, come descritto nella [documentazione per il modulo standard di Python `ssl`](http://docs.python.org/3/library/ssl.html#self-signed-certificates). Per impedire attacchi MITM, sarà anche necessario aggiungere il certificato generato all'archivio radice della CA nel computer Windows in cui è in esecuzione PTVS. Questa operazione può essere eseguita con Gestione certificati (Certmgr. msc), come descritto in [How do I export certificates and/or private keys?](https://answers.microsoft.com/en-us/windows/forum/windows_10-security/how-do-i-export-certificates-andor-private-keys/7722900a-e848-4076-bc50-9e2f5e3c66ac) (Qual è la procedura per esportare certificati e/o chiavi private?). Si noti che sarà necessario disporre di un file di certificato separato da importare, ovvero non combinato con la chiave privata in un singolo file. 

Dopo aver generato e registrato i file del certificato e della chiave privata, sarà necessario aggiornare la chiamata a `enable_attach` nello script per usarli. Questa operazione viene eseguita con i parametri `certfile` e `keyfile`, che hanno lo stesso significato valido per la funzione Python standard `ssl.wrap_socket`. Ad esempio, se il file di certificato è denominato `my_cert.cer` e i file della chiave è denominato `my_cert.key`, usare: 

```python
ptvsd.enable_attach(secret='my_secret', certfile='my_cert.cer', keyfile='my_cert.key')
```

Il processo di collegamento è esattamente identico a quello descritto in precedenza, tranne per il fatto che invece di usare lo schema `tcp://` nel qualificatore si usa `tcps://`: 

![Scelta del trasporto di debug remoto con SSL](media/remote-debugging-qualifier-ssl.png)

Se il certificato non è stato aggiunto all'archivio radice della CA, verrà visualizzato un messaggio di avviso: 

![Avviso per il certificato SSL](media/remote-debugging-ssl-warning.png)

È possibile scegliere di ignorare l'avviso e continuare con il debug. Il canale verrà comunque crittografato per evitare intercettazioni. Ignorando l'avviso, però, ci si espone ad attacchi MITM.

