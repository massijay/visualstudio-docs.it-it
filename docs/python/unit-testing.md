---
title: Unit test per Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3ad6523-5a4e-4209-8977-adc2da305df2
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
ms.openlocfilehash: 2597583912c7694495617c53839f41aa13cda871
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---

# <a name="setting-up-unit-testing-for-python-code"></a>Configurazione degli unit test per il codice Python

Gli unit test sono parti di codice che testano altre unità di codice in un'applicazione, in genere funzioni isolate, classi e così via. Quando l'applicazione supera tutti i relativi unit test, è possibile supporre con una certa attendibilità che la relativa funzionalità di basso livello sia corretta.

In Python gli unit test vengono usati frequentemente per convalidare gli scenari durante la progettazione di un programma. Il supporto di Python in Visual Studio include l'individuazione, l'esecuzione e il debug di unit test direttamente all'interno del contesto del processo di sviluppo, invece di dover eseguire separatamente tali operazioni.

Questo argomento illustra brevemente le funzionalità degli unit test in Visual Studio con Python. Per altre informazioni di carattere generale sull'esecuzione di unit test, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

## <a name="discovering-and-viewing-tests"></a>Individuazione e visualizzazione di test

Per convenzione, Visual Studio identifica i test come metodi il cui nome inizia con "test". Per verificarlo, eseguire le operazioni seguenti:

1. Aprire un [progetto Python](python-projects.md) caricato in Visual Studio, fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi > Nuovo elemento** e quindi selezionare **Unit test Python** seguito da **Aggiungi**.

1. Verrà creato un file test1.py contenente il codice che importa il modulo standard `unittest`, deriva una classe di test da `unittest.TestCase` e richiama `unittest.main()` se si esegue lo script direttamente:

  ```python
  import unittest

  class Test_test1(unittest.TestCase):
      def test_A(self):
          self.fail("Not implemented")

  if __name__ == '__main__':
      unittest.main()
  ```

1. Se necessario, salvare il file e aprire Esplora test con il comando di menu **Test > Windows > Esplora test**.

1. Esplora test cercherà il progetto per i test e li visualizzerà come illustrato di seguito. Fare doppio clic su un test per aprirne il file di origine.

    ![Esplora test con test_A predefinito](~/python/media/unit-test-A.png)

1. Via via che si aggiungono altri test al progetto, è possibile organizzare la visualizzazione in Esplora test tramite il menu Raggruppa per della barra degli strumenti:

    ![Menu Raggruppa per della barra degli strumenti in Esplora test](~/python/media/unit-test-group-menu.png)

1. È anche possibile immettere testo nel campo di ricerca per filtrare i test in base al nome.

Per altre informazioni sul modulo `unittest` e sulla scrittura di test, vedere la [documentazione di Python 2.7](https://docs.python.org/2/library/unittest.html) oppure la [documentazione di Python 3.4](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Esecuzione di test

In Esplora test è possibile eseguire test in diversi modi:

- L'opzione **Esegui tutto** esegue chiaramente tutti i test visualizzati, tenendo conto degli eventuali filtri applicati.
- Il menu **Esegui** include i comandi per eseguire in gruppo test non superati, superati o non eseguiti.
- È possibile selezionare uno o più test, fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati**.

I test vengono eseguiti in background ed Esplora test aggiorna lo stato di ogni test non appena viene completato:

- I test superati sono contraddistinti da un segno di spunta verde, nonché dall'indicazione del tempo necessario per eseguirli:

    ![test_A superato](~/python/media/unit-test-A-pass.png)

- I test non superati sono contraddistinti da una croce rossa e includono un collegamento **Output** che mostra l'output della console e l'output di `unittest` restituito dall'esecuzione dei test:

    ![test_A non superato](~/python/media/unit-test-A-fail.png)

    ![test_A non superato con motivo](~/python/media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Debug di test

Dal momento che gli unit test sono parti di codice, sono soggetti a bug esattamente come qualsiasi altro tipo di codice. Può quindi essere necessario talvolta eseguirli in un debugger, in cui è possibile impostare punti di interruzione, esaminare le variabili ed eseguire il codice istruzione per istruzione. Visual Studio include anche strumenti di diagnostica.

Per avviare il debug, impostare un punto di interruzione iniziale nel codice, fare clic con il pulsante destro del mouse sul test (o su una selezione) in Esplora test e quindi scegliere **Esegui debug test selezionati**. Visual Studio avvierà il debugger di Python come farebbe per il codice dell'applicazione.

![Debug di un test](~/python/media/unit-test-debugging.png)

A seconda della versione di Visual Studio, è anche possibile usare i comandi **Analizza code coverage per i test selezionati** ed **Esegui profilatura test**. Vedere la [matrice delle funzionalità](python-in-visual-studio.md#features-matrix).

### <a name="known-issues"></a>Problemi noti

- Quando si avvia il debug, Visual Studio sembra avviare e arrestare il debug e quindi avviarlo di nuovo. Si tratta di una condizione prevista.
- Durante il debug di più test, ognuno di essi viene eseguito in modo indipendente e questo causa l'interruzione della sessione di debug.
- Di tanto in tanto Visual Studio non riesce ad avviare un test durante il debug. In genere, il problema si risolve ripetendo il debug del test.
- Durante il debug, è possibile uscire da un test nell'implementazione di `unittest`. In genere, il passaggio successivo verrà eseguito alla fine del programma e arresterà il debug.
