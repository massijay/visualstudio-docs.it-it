---
title: REPL IPython in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
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
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>Uso di Python nella finestra interattiva

La finestra interattiva di Visual Studio in modalità IPython costituisce un ambiente di sviluppo interattivo avanzato e al contempo intuitiva avanzato e semplice da usare che include funzionalità di elaborazione parallela interattiva. In questo argomento verrà illustrato l'uso di IPython nella finestra interattiva di Visual Studio. A questo scopo, è necessario aver installato l'ambiente [Anaconda](https://www.continuum.io), che include IPython e le librerie necessarie.

> [!Note]
> IronPython non supporta IPython, anche se è possibile selezionarlo nel modulo delle opzioni interattive. È possibile votare a favore della [richiesta di funzionalità](https://github.com/Microsoft/PTVS/issues/84) o implementarla se si preferisce.

1. Per verificare che il pacchetto IPython sia installato correttamente, passare alla directory di installazione di Python e avviare IPython in modalità Pylab:

  ```bash
  ipython --pylab
  ```

1. Immettere quanto segue:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. Se la configurazione è corretta, l'output visualizzato sarà simile al seguente:

    ![Output di configurazione di IPython ](media/ipython-repl-01.png)

1. Aprire Visual Studio, passare alla finestra Ambienti Python (**Visualizza > Altre finestre > Ambienti Python**) e selezionare l'ambiente Python.
1. Osservare la scheda **pip** e assicurarsi che l'elenco includa `IPython` e `matplotlib`. In caso contrario, installarli qui.
1. Selezionare la scheda **Panoramica**, selezionare **Configura opzioni interattive**, impostare **Modalità interattiva** su IPython e fare clic su **OK**:

    ![Impostazione della modalità interattiva su IPython](media/ipython-repl-02.png)

1. Selezionare **Apri finestra interattiva** per visualizzare la finestra interattiva in modalità IPython con PyLab. Se è stata appena cambiata la modalità interattiva, potrebbe essere necessario reimpostare la finestra:

    ![Finestra interattiva in modalità IPython](media/ipython-repl-03.png)

1. Immettere il codice seguente:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Dopo aver immesso l'ultima riga, verrà visualizzato un grafico inline, che è possibile ridimensionare trascinando nell'angolo inferiore destro se si desidera.

    ![Grafico inline nella finestra interattiva](media/ipython-repl-04.png)

1. Invece di digitare in REPL, è possibile scrivere codice nell'editor, selezionarlo, fare clic con il pulsante destro del mouse e scegliere il comando **Invia alla finestra** (CTRL+E, E). Provare a incollare il codice seguente nell'editor, selezionandolo con CTRL+A e quindi inviandolo alla finestra interattiva. Si noti che Visual Studio invia il codice alla finestra interattiva in un unico blocco per evitare che vengano visualizzati grafici intermedi o parziali.

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set will be colored cyan.
        cs = [c] * len(xs) 
        cs[0] = 'c' 
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X') 
    ax.set_ylabel('Y') 
    ax.set_zlabel('Z') 
    plt.show()
    ```

    ![Invio di codice dall'editor alla finestra interattiva](media/ipython-repl-05.png)

1. Per visualizzare i grafici all'esterno della finestra interattiva, eseguire il codice invece di usare il comando **Debug > Avvia senza eseguire debug**.
    
1. In IPython sono disponibili numerose funzionalità utili, ad esempio l'escape alla shell di sistema, la sostituzione delle variabili, l'acquisizione di output e così via. Per altre informazioni, vedere la Guida di riferimento di IPython:

    ![Escape alla shell di sistema](media/ipython-repl-06.png)

1. È anche possibile eseguire IPython in modalità "blocco appunti", per usare come area di disegno qualsiasi browser in qualsiasi sistema operativo. Il motore di back-end di IPython può essere locale, ovvero disponibile nel computer, oppure remoto. Azure include il supporto per eseguire [IPython in una macchina virtuale Windows o Linux](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook). Vedere anche [Azure Notebooks Preview](https://notebooks.azure.com) per accedere a blocchi appunti Jupyter gratuiti come servizio in Azure:

    ![Modalità blocco appunti di IPython](media/ipython-repl-07.png)

