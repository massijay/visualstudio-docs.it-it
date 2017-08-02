---
title: Uso di PyLint in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
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
ms.sourcegitcommit: 9328c347d548a03a536cea16bd5851817c03d5a2
ms.openlocfilehash: c8bfaf9f20e7fecb3633ca101170b0f3e686aa53
ms.lasthandoff: 04/10/2017

---

# <a name="using-pylint-to-check-python-code"></a>Uso di PyLint per controllare il codice Python

[PyLint](https://www.pylint.org/), uno strumento molto diffuso che verifica la presenza di errori nel codice Python e promuove buone prassi di scrittura del codice per Python, è integrato in Visual Studio per i progetti Python.

È sufficiente fare clic con il pulsante destro del mouse su un progetto Python in Esplora soluzioni e scegliere **Python > Esegui PyLint**:

![Comando PyLint nel menu di scelta rapida per i progetti Python](~/python/media/code-pylint-command.png)

Quando si usano i comandi viene richiesto di installare PyLint nell'ambiente attivo, se necessario.

Gli avvisi e gli errori di PyLint vengono Visualizzati nella finestra Elenco errori:

![Elenco errori di PyLint](~/python/media/code-pylint-error-list.png)

È possibile fare doppio clic su un errore per passare direttamente al codice sorgente che ha generato il problema.

> [!Tip]
> Vedere le [informazioni di riferimento sulle funzionalità di PyLint](https://pylint.readthedocs.io/en/latest/reference_guide/features.html) per un elenco dettagliato di tutti i messaggi di output di PyLint.

## <a name="setting-pylint-command-line-options"></a>Impostazione delle opzioni della riga di comando di PyLint

Nella sezione dedicata alle [opzioni della riga di comando](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) della documentazione di PyLint viene descritto come controllare il comportamento di PyLint tramite un file di configurazione `.pylintrc`. Questo file può essere posizionato nella radice di un progetto di Python in Visual Studio o in altre posizioni, a seconda del contesto in cui si vogliono applicare tali impostazioni.

Ad esempio, per eliminare gli avvisi "missing docstring" illustrati nella figura precedente con un file `.pylintrc` in un progetto, eseguire le operazioni seguenti:

1. Nella riga di comando passare alla radice del progetto (in cui è disponibile il file `.pyproj`) ed eseguire il comando seguente per generare un file di configurazione impostato come commento:

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. In Esplora soluzioni di Visual Studio, fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi > Elemento esistente**, individuare e selezionare il nuovo file `.pylintrc` e selezionare **Aggiungi**.

1. Aprire il file per la modifica. Verrà visualizzata un'ampia gamma di opzioni disponibili per l'utilizzo. Per disabilitare un avviso, individuare la sezione `[MESSAGES CONTROL]` e quindi individuare l'impostazione `disable` in tale sezione. Si noterà una stringa lunga di messaggi specifici, a cui è possibile aggiungere qualsiasi avviso. In questo esempio, aggiungere `,missing-docstring` (inclusa la virgola di delimitazione).

1. Salvare il file `.pylintrc` ed eseguire di nuovo PyLint per verificare che gli avvisi vengono ora soppressi.
