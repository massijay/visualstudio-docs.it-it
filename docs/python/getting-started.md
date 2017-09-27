---
title: Introduzione a Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: d0a5b44962b0cfbe549453b1760a38237de7e6ab
ms.openlocfilehash: 420af3d78a514a7e6b6ded186c204ad8301c4c85
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Introduzione a Python in Visual Studio

Dopo avere installato Visual Studio con il carico di lavoro Python (Visual Studio 2017) o con Python Tools for Visual Studio (Visual Studio 2015 e versioni precedente), si è pronti per esplorare l'esperienza di sviluppo con Python. (Vedere [Installazione](installation.md) se necessario.)

Questa procedura dettagliata descrive come creare una nuova applicazione Python vuota, scegliere un ambiente Python da usare e quindi come scrivere codice per osservare il funzionamento di IntelliSense. Si utilizzerà quindi la finestra REPL interattiva per un breve periodo per creare altro codice, quindi si completerà il programma e lo si eseguirà da solo e nel debugger.

> [!Note]
> Questa procedura dettagliata illustra l'esperienza di Python in Visual Studio 2017. In altre versioni l'esperienza è simile, ma con alcune possibili differenze nei dettagli.

## <a name="create-a-new-python-project"></a>Creare un nuovo progetto Python

Il supporto per Python in Visual Studio include vari [modelli di progetto](python-projects.md) per iniziare con diversi tipi di progetti, incluse applicazioni Web che usano i framework Bottle, Flask e Django insieme a Servizi cloud di Azure. Per gli scopi di questa procedura dettagliata, tuttavia, si inizierà con un progetto vuoto.

1. In Visual Studio selezionare **File > Nuovo progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto**. Qui è possibile cercare e selezionare un modello e specificare la cartella in cui creare il progetto.

1. I modelli di Python sono disponibili in **Modelli > Altri linguaggi > Python** a sinistra oppure cercando "Python":

    ![Finestra di dialogo Nuovo progetto con visualizzati i progetti Python](media/getting-started-new-project.png)

1. Selezionare il modello "Python Application" (Applicazione Python), specificare una cartella per il progetto e selezionare **OK**. Se si vuole creare immediatamente un repository locale per il progetto, selezionare anche l'opzione **Aggiungi al controllo del codice sorgente**.

    > [!Tip]
    > Il modello "From existing Python Code" (Da codice Python esistente) consente di creare rapidamente un progetto di Visual Studio da una cartella che contiene già codice Python, invece di creare un nuovo progetto vuoto e importare codice esistente al suo interno.

1. Dopo qualche secondo, il progetto viene aperto nella finestra Esplora soluzioni di Visual Studio. In questa finestra è possibile esplorare i file e cartelle del progetto, oltre a gestire gli ambienti.

    ![Esplora soluzioni con un progetto Python](media/getting-started-solution-explorer-1.png)

1. Espandere il nodo **Ambienti Python**. Verrà visualizzato l'interprete Python predefinito corrente per il progetto. Se si espande anche il nodo dell'interprete, viene visualizzato un elenco delle librerie disponibili in tale ambiente:

    ![Ambiente Python visualizzato in Esplora soluzioni](media/getting-started-solution-explorer-2.png)

1. Se si usa Visual Studio 2015 o una versione precedente, non è disponibile un interprete Python installato per impostazione predefinita. Per questo processo, fare riferimento a [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Selezione e installazione di interpreti Python).

### <a name="going-deeper"></a>Approfondimenti

- [Python Projects in Visual Studio (Progetti Python in Visual Studio)](python-projects.md)
- [Modelli di progetti Web](template-web.md)
- [Modelli di progetti Web Django](template-django.md)
- [Modello del servizio cloud di Azure](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Scrittura ed esecuzione del codice

1. Dopo aver creato un nuovo progetto "Python Application" (Applicazione Python), nell'editor di Visual Studio viene aperto un file vuoto predefinito denominato `PythonApplication1.py`. Per rinominarlo, fare clic con il pulsante destro del mouse sul file in Esplora soluzioni e scegliere **Rinomina**, quindi cambiare il nome in `hello.py`.

1. Iniziare a digitare `print("Hello world")` e notare che IntelliSense di Visual Studio visualizza le opzioni di completamento automatico durante la digitazione. L'opzione con contorno nell'elenco a discesa è il completamento predefinito usato quando si preme TAB. Il completamento è utile soprattutto in presenza di istruzioni o identificatori più lunghi.

    ![Popup di completamento automatico IntelliSense](media/getting-started-coding-1.png)

1. In IntelliSense vengono mostrate informazioni diverse a seconda dell'istruzione usata, della funzione chiamata e così via. Con la funzione `print`, quando si digita `(` per impostare la chiamata, vengono visualizzate informazioni complete sulla sintassi della funzione e viene visualizzato l'argomento corrente che è necessario specificare (**value** in questo caso):

    ![Popup di completamento automatico IntelliSense per una funzione](media/getting-started-coding-2.png)

1. Completare l'istruzione in modo che corrisponda alla seguente:

  ```python
  print("Hello world")
  ```

1. Per eseguire il codice, premere F5 o selezionare la voce di menu **Debug > Avvia debug**.

    > [!Note]
    > Se viene visualizzato un messaggio in Visual Studio 2015 o versioni precedenti per segnalare che non sono disponibili interpreti, vedere [Selecting and installing a Python interpreter](python-environments.md#selecting-and-installing-python-interpreters) (Selezione e installazione di un interprete Python) perché in queste versioni non ne viene installato uno per impostazione predefinita.

1. Visual Studio esegue il codice usando l'ambiente predefinito nel progetto e visualizza i risultati in una finestra di comando. Premere un tasto per chiudere la finestra e terminare la sessione di debug.

    ![Pulsante Avvia sulla barra degli strumenti di debug](media/getting-started-coding-4.png)

1. Oltre a istruzioni e funzioni, IntelliSense offre completamenti per le istruzioni `import`. I completamenti delle istruzioni import consentono di individuare facilmente i moduli disponibili nell'ambiente e i membri disponibili in ogni modulo. Nell'editor eliminare la riga `print` e iniziare a digitare `import`. Viene visualizzato un elenco di moduli:

    ![IntellSense che mostra i moduli disponibili per un'istruzione import](media/getting-started-coding-5.png)

1. Completare la riga digitando o selezionando `sys`.

1. Nella riga successiva digitare `from` per visualizzare nuovamente un elenco di moduli:

    ![IntellSense che mostra i moduli disponibili per un'istruzione from](media/getting-started-coding-6.png)

1. Selezionare o digitare `math`, quindi continuare a digitare uno spazio e `import` per visualizzare i membri del modulo:

    ![IntellSense che mostra i membri del modulo](media/getting-started-coding-7.png)

1. Completare l'importazione dei membri `sin`, `cos` e `radians`, osservando i completamenti automatici disponibili per ogni membro. Al termine, il codice dovrebbe essere simile al seguente:

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> I completamenti si basano su sottostringhe durante la digitazione, cercando corrispondenze per parti di parole, lettere all'inizio delle parole e anche caratteri saltati. Per altri dettagli, vedere [Modifica del codice - Completamenti](code-editing.md#completions).

Nel passaggio successivo verrà illustrato l'uso della finestra REPL interattiva per scrivere codice che è possibile testare immediatamente senza eseguire il debugger.

### <a name="going-deeper"></a>Approfondimenti

- [Modifica del codice](code-editing.md)
- [Formattazione del codice](code-formatting.md)
- [Refactoring del codice](code-refactoring.md)
- [Uso di PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>Uso della finestra interattiva REPL

La finestra interattiva di Visual Studio per Python offre un'esperienza completa REPL (Read–Eval–Print Loop), che consente di ridurre notevolmente il normale ciclo di modifica-compilazione-debug. È simile all'esperienza REPL della riga di comando di Python, ma offre alcune funzionalità aggiuntive, come illustrato di seguito.

1. Per aprire la finestra interattiva, selezionare **View > Other Windows > Python Interactive Windows** (Visualizza > Altre finestre > Finestre interattive Python) dal menu principale di Visual Studio. La finestra verrà visualizzata con il consueto prompt REPL di Python >>>. Si noti che è possibile usare il menu a discesa sulla barra degli strumenti per cambiare ambiente in qualsiasi momento:

    ![Finestra interattiva di Python](media/getting-started-interactive-1.png)

1. Immettere alcune istruzioni (ad esempio `print("hello")`) ed espressioni (ad esempio `123/567`) per visualizzare i risultati immediati:

    ![Risultati immediati nella finestra interattiva di Python](media/getting-started-interactive-2.png)

1. Quando si inizia a scrivere un'istruzione su più righe, ad esempio una definizione di funzione, la finestra interattiva mostra il prompt ... per le righe di continuazione, per le quali è disponibile il rientro automatico, diversamente dall'ambiente REPL dalla riga di comando:

    ![Finestra interattiva di Python con continuazione dell'istruzione](media/getting-started-interactive-3.png)

1. La finestra interattiva offre una cronologia completa di tutti gli elementi immessi e migliora l'ambiente REPL dalla riga di comando con elementi della cronologia su più righe. Ad esempio, è possibile richiamare facilmente l'intera definizione della funzione `f` di sopra come singola unità e modificare in modo semplice il nome in `make_double`, invece di dover ricreare la funzione riga per riga.

1. Un'altra funzionalità utile è la possibilità di inviare rapidamente più righe di codice da una finestra dell'editor alla finestra interattiva, in cui è possibile usare questo codice nell'ambiente rapido REPL, piuttosto che scrivere altro codice da eseguire nel debugger. Per un esempio pratico di questa funzionalità, iniziare aggiungendo il codice seguente al file hello.py aperto nell'editor:

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Selezionare tutto il codice in hello.py (incluse le istruzioni `import`), fare clic con il pulsante destro del mouse e scegliere **Send to Interactive** (Invia a finestra interattiva) (CTRL+INVIO). Il codice viene incollato immediatamente nella finestra interattiva ed eseguito. Dato che il codice definisce una funzione, è possibile testare rapidamente la funzione chiamandola più volte:

    ![Invio di codice alla finestra interattiva](media/getting-started-interactive-4.png)

1. Anche l'uso di Ctrl + Invio con il cursore in un'unica riga nell'editor è un modo semplice per esaminare il codice. Ctrl + Invio consente di eseguire la riga corrente nella finestra interattiva, spostando quindi automaticamente il cursore alla riga successiva. Premendo Ctrl + Invio più volte, quindi, è possibile eseguire tutto il codice in un file.

1. In Visual Studio 2017 è possibile incollare più righe direttamente nella finestra interattiva. Nelle versioni precedenti è necessario incollare le righe in una finestra dell'editor, selezionarle e quindi usare **Invia a Interactive**. Quando il codice viene incollato, la finestra interattiva lo esegue, come è possibile vedere nella figura seguente:

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Incollare più righe di codice tramite l'invio alla finestra interattiva](media/getting-started-interactive-5.png)

1. Dato che la definizione della funzione è presente nella cronologia REPL come singola unità, è facile tornare indietro e apportare qualsiasi modifica, per poi testare di nuovo la funzione.

1. Quando il codice scritto nella finestra interattiva risulta soddisfacente, è possibile selezionarlo, fare clic con il pulsante destro del mouse, scegliere **Copia codice** e quindi incollare il codice nell'editor. Il comando **Copia codice** omette automaticamente qualsiasi output, nonché il testo di prompt >>> e ... Ad esempio, se si usa il comando con la selezione illustrata di seguito:

  ![Comando Copia codice nella finestra interattiva](media/getting-started-interactive-6.png)

  viene incollato solo quanto segue:

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Infine, la finestra interattiva offre una serie di metacomandi che consentono di caricare i file, reimpostare l'ambiente senza perdere la cronologia e inserire commenti mentre si procede. Per altri dettagli, vedere i [metacomandi per la finestra interattiva](interactive-repl.md#meta-commands).

### <a name="going-deeper"></a>Approfondimenti

- [Uso della finestra interattiva](interactive-repl.md)
- [Uso di REPL IPython](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>Esecuzione del codice nel debugger

Oltre a consentire di gestire i progetti, rendendo disponibili un'esperienza di modifica completa e la finestra interattiva, Visual Studio offre il supporto completo del debug per il codice Python.

1. Modificare il codice nel file hello.py in modo che corrisponda al seguente:

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. Controllare che il codice funzioni correttamente. A tale scopo, premere F5 o selezionare il comando di menu **Debug > Avvia debug**. Il comando esegue il codice nel debugger. Dato che non sono impostati punti di interruzione, tuttavia, stampa semplicemente un motivo ondulato per alcune iterazioni. Se si preme un tasto a questo punto, la finestra di output viene chiusa.

    > [!Tip]
    > Per chiudere la finestra di output automaticamente dopo il completamento del programma, sostituire la chiamata `main()` con il codice seguente:
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > In alternativa, se si verificano situazioni in cui la finestra di output si chiude automaticamente quando non lo si vuole, fare clic con il pulsante destro del mouse sul progetto, selezionare **Proprietà**, selezionare la scheda **Debug** e quindi aggiungere `-i` al campo **Argomenti dell'interprete**. Questo argomento fa sì che l'interprete passi in modalità interattiva dopo il completamento di un programma, mantenendo la finestra aperta fino a quando non viene premuto CTRL+Z, INVIO per uscire.

1. Impostare un punto di interruzione sulla prima riga della funzione `main` facendo clic nel margine grigio a sinistra della riga oppure posizionare il cursore nella riga e usare il comando **Debug > Attiva/disattiva punto di interruzione** (F9). Sul margine grigio viene visualizzato un punto rosso per indicare il punto di interruzione, come indicato dalla freccia blu di seguito:

    ![Impostazione di un punto di interruzione](media/getting-started-debugging-1.png)

1. Avviare di nuovo il debugger. Si può vedere che l'esecuzione del codice si interrompe in corrispondenza della riga con il punto di interruzione. È così possibile analizzare lo stack di chiamate ed esaminare le variabili locali nella finestra Variabili locali:

    ![Esperienza dell'interfaccia utente per i punti di interruzione per Python](media/getting-started-debugging-2.png)

1. Esaminare alcune iterazioni del ciclo `for` riga per riga usando F10, il comando **Debug > Esegui istruzione/routine** o il pulsante della barra degli strumenti Esegui istruzione/routine. Esegui istruzione/routine significa che il debugger esegue ogni chiamata a `make_dot_string`, ma si ferma all'interno di tale funzione solo se si imposta un punto di interruzione.

1. Sulla barra degli strumenti i tre pulsanti per l'esecuzione riga per riga illustrati di seguito sono, da sinistra a destra: Esegui istruzione, Esegui istruzione/routine ed Esci da istruzione/routine:

    ![Pulsanti della barra degli strumenti per l'esecuzione riga per riga](media/getting-started-debugging-3.png)

1. Eseguire ora l'istruzione `make_dot_string` con il comando Esegui istruzione (F11). Si noti il passaggio dal ciclo `for` a tale funzione. Eseguendo di nuovo il comando si torna al ciclo `for`, ma se la funzione contiene altre righe, si passa a ognuna di esse, una alla volta. Se ci si trova in una funzione e si vuole eseguire il resto delle righe e poi tornare al codice chiamante, usare il comando Esci da istruzione/routine (MAIUSC+F11).

1. Per continuare a eseguire il codice fino a raggiungere il punto di interruzione successivo, o fino alla fine del programma, premere di nuovo F5, selezionare il pulsante **Continua** sulla barra degli strumenti oppure scegliere **Debug > Continua**. Dato che il ciclo `for` contiene un punto di interruzione, l'esecuzione verrà interrotta nell'iterazione successiva.

1. Eseguire in questo modo centinaia di iterazioni di un ciclo può essere noioso, quindi è possibile aggiungere una condizione per il punto di interruzione impostato in precedenza, in modo che l'esecuzione venga interrotta solo quando il valore di `i` supera un determinato valore, ad esempio 1600. Per impostare una condizione, fare clic con il pulsante destro del mouse sul punto rosso del punto di interruzione e scegliere **Condizione...**. Nella finestra Impostazioni del punto di interruzione visualizzata immettere `i > 1600` come espressione e selezionare **Chiudi**. A questo punto premere F5 per continuare. Il programma verrà eseguito per un po' prima di interrompersi nuovamente. 

    ![Impostazione di una condizione per il punto di interruzione](media/getting-started-debugging-4.png)

1. Per completare il programma, è possibile attivare nuovamente il punto di interruzione e premere F5. Visual Studio ritorna alla modalità di modifica al termine del debug.

### <a name="going-deeper"></a>Approfondimenti

- [Debug](debugging.md).
- Vedere anche [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) per la documentazione completa sulle funzionalità di debug di Visual Studio.

## <a name="next-steps"></a>Passaggi successivi

Oltre ai collegamenti "Approfondimenti" indicati in precedenza, gli argomenti seguenti trattano altre funzionalità dell'esperienza di Python in Visual Studio:

- Per informazioni su come Visual Studio si connette a Servizio app di Azure, vedere [Publishing a Python web application to Azure](publishing-to-azure.md) (Pubblicazione di un'applicazione Web Python in Azure).
- Per scoprire come gestire ambienti diversi, sia globalmente che per singoli progetti, inclusi gli ambienti virtuali, vedere [Python Environments](python-environments.md) (Ambienti Python).
- Visual Studio offre la possibilità di eseguire il debug dell'applicazione in server remoti, come spiegato in [Debug remoto multipiattaforma](debugging-cross-platform-remote.md) e [Debug remoto in Azure](debugging-azure-remote.md).
- È possibile valutare le prestazioni del codice Python usando la funzionalità di [profilatura di Visual Studio](profiling.md).
- Gli unit test scritti in Python possono essere integrati direttamente in Esplora test di Visual Studio, come descritto in [Setting Up Unit Testing for Python Code](unit-testing.md) (Configurazione di unit test per il codice Python).
- [Corsi gratuiti per Python in Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions (Domande principali su Python) alla Microsoft Virtual Academy](https://aka.ms/mva-top-python-questions)

