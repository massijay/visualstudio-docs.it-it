---
title: "Risoluzione dei problemi di code coverage | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Risoluzione dei problemi di code coverage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento di analisi della copertura del codice in Visual Studio raccoglie dati per assembly nativo e gestito \(file .dll o .exe\).  Tuttavia, in alcuni casi, la finestra dei risultati della copertura del codice visualizza un errore simile a "Generati risultati vuoti: ...." Esistono vari motivi possibili per cui questo può verificarsi.  Questo argomento è progettato per aiutare a risolvere quei problemi.  
  
## Cosa si dovrebbe vedere  
 Se si sceglie un comando **Analizza code coverage** dal menu Test e se la compilazione e i test vengono eseguiti correttamente, allora sarà visualizzato un elenco di risultati nella finestra di copertura del codice.  Potrebbe essere necessario espandere gli elementi per visualizzare il dettaglio.  
  
 ![Risultati del code coverage con colorazione](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Per altre informazioni, vedere [Utilizzo di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## Cause possibili per la restituzione di nessun risultato o di risultati obsoleti  
  
### L'edizione di Visual Studio in uso è corretta?  
 È necessario Visual Studio Enterprise.  
  
### Nessun test è stato eseguito  
 Analisi  
 Verificare la finestra di output.  Nell'elenco a discesa **Mostra output da**, scegliere **Test**.  Verificare se sono presenti avvisi o errori registrati.  
  
 Descrizione  
 L'analisi del code coverage viene effettuata mentre i test sono in esecuzione.  Include solo gli assembly caricati in memoria quando i test vengono eseguiti.  Se nessun test viene eseguito allora il code coverage non ha nulla da riportare.  
  
 Risoluzione  
 In Esplora test, scegliere **Esegui tutto** per verificare che i test vengano eseguiti correttamente.  Correggere tutti gli errori prima di utilizzare **Analizza code coverage**.  
  
### Si sta cercando un risultato precedente  
 Quando si modificano e si rieseguono i test, i risultati di un code coverage precedente possono rimanere visibile, inclusa la colorazione del codice dell'esecuzione precedente.  
  
1.  Eseguire Analizza code coverage.  
  
2.  Verificare che sia stato selezionato il set di risultati più recente nella finestra dei risultati del code coverage.  
  
### I file con estensione pdb \(simbolo\) non sono disponibili  
 Analisi  
 Aprire la cartella di destinazione della compilazione \(in genere bin\\debug\) e verificare che per ogni assembly esista un file con estensione pdb nella stessa directory del file con estensione dll o exe.  
  
 Descrizione  
 Il motore di code coverage richiede che ogni assembly abbia un proprio file con estensione pdb associato accessibile durante l'esecuzione del test.  Se non esiste alcun file con estensione pdb per un particolare assembly, tale assembly non verrà analizzato.  
  
 Il file con estensione pdb deve essere generato dalla stessa compilazione dei file con estensione dll o exe.  
  
 Risoluzione  
 Verificare che le impostazioni di compilazione generino il file con estensione pdb.  Se i file con estensione pdb non vengono aggiornati quando il progetto viene compilato, aprire le proprietà del progetto, selezionare la pagina **Compila**, scegliere **Avanzate** e controllare **Informazioni di debug**.  
  
 Se i file con estensione pdb e dll o exe sono in posizioni diverse, copiare il file con estensione pdb nella stessa directory.  È inoltre possibile configurare il motore di code coverage per cercare i file con estensione pdb in un'altra posizione.  Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
### Utilizzo di un binario instrumentato o ottimizzato  
 Analisi  
 Determinare se il binario è stato sottoposto a qualche forma di ottimizzazione avanzata, come l'ottimizzazione PGO, o è stato instrumentato da uno strumento di profilatura come vsinstr.exe o vsperfmon.exe.  
  
 Descrizione  
 Se l'assembly è già stato instrumentato o ottimizzato da un altro strumento di profilatura, l'assembly viene omesso dall'analisi di code coverage.  
  
 L'analisi di code coverage non può essere eseguita su tali assembly.  
  
 Risoluzione  
 Disattivare l'ottimizzazione e usare una nuova compilazione.  
  
### Codice non gestito \(.NET\) o codice nativo \(C\+\+\)  
 Analisi  
 Verificare che vengano eseguiti alcuni test sul codice gestito o C\+\+.  
  
 Descrizione  
 L'analisi di code coverage in Visual Studio è disponibile solo nel codice gestito e nativo \(C\+\+\).  Se si utilizzano strumenti di terze parti, il codice può essere eseguito parzialmente o totalmente su una piattaforma diversa.  
  
 Risoluzione  
 Non disponibile.  
  
### L'assembly è stato installato da NGen  
 Analisi  
 Verificare che l'assembly non venga caricato dalla cache delle immagini native.  
  
 Descrizione  
 Per motivi di prestazioni, gli assembly di immagini native non vengono analizzate.  Per altre informazioni, vedere [Ngen.exe \(Native Image Generator\)](../Topic/Ngen.exe%20\(Native%20Image%20Generator\).md).  
  
 Risoluzione  
 Utilizzare una versione MSIL dell'assembly.  Non elaborarlo con NGen.  
  
### File personalizzato con estensione runsettings con sintassi non valida  
 Analisi  
 Un file personalizzato con estensione runsettings potrebbe contenere un errore di sintassi.  
  
 Di conseguenza, nessun code coverage verrà eseguito.  La finestra di code coverage non viene visualizzata alla fine dell'esecuzione del test oppure vengono visualizzati risultati obsoleti.  
  
 Descrizione  
 È possibile eseguire gli unit test con un file personalizzato con estensione runsettings per configurare le opzioni di code coverage.  Le opzioni consentono di includere o escludere i file.  Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
 Risoluzione  
 Esistono due possibili tipi di errori:  
  
-   **Errore XML**  
  
     Aprire il file con estensione runsettings nell'editor XML di Visual Studio.  Individuare le indicazioni degli errori.  
  
-   **Errore di espressione regolare**  
  
     Ogni stringa del file è un'espressione regolare.  Rivederle singolarmente per individuare gli errori, in particolare cercare:  
  
    -   Parentesi non corrispondenti \(...\) o parentesi non precedute da un carattere di escape \\\(...  \\\).  Se si desidera trovare la corrispondenza con una parentesi nella stringa di ricerca, è necessario utilizzare caratteri di escape.  Ad esempio, per trovare la corrispondenza con una funzione, usare `.*MyFunction\(double\)`  
  
    -   L'asterisco o il segno più all'inizio di un'espressione.  Per cercare una stringa di caratteri, utilizzare un punto seguito da un asterisco: `.*`  
  
### File personalizzato con estensione runsettings con esclusioni non corrette  
 Analisi  
 Se si utilizza un file personalizzato con estensione runsettings, assicurarsi di sia incluso nell'assembly.  
  
 Descrizione  
 È possibile eseguire gli unit test con un file personalizzato con estensione runsettings per configurare le opzioni di code coverage.  Le opzioni consentono di includere o escludere i file.  Per altre informazioni, vedere [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
 Risoluzione  
 Rimuovere tutti i nodi `Include` dal file con estensione runsettings quindi rimuovere tutti i nodi `Exclude`.  Se in tal modo si risolve il problema, riportare i nodi nelle fasi.  
  
 Assicurarsi che il nodo DataCollectors specifichi Code coverage.  Confrontarlo con l'esempio in [Personalizzazione dell'analisi code coverage](../test/customizing-code-coverage-analysis.md).  
  
## Il codice verrà sempre visualizzato come parzialmente non analizzato  
  
### Il codice di inizializzazione nelle DLL native viene eseguito prima della strumentazione  
 Analisi  
 Nel codice nativo collegato in modo statico, la parte della funzione di inizializzazione **DllMain** e il codice che chiama viene talvolta visualizzato come non analizzato anche se è stato eseguito.  
  
 Descrizione  
 Lo strumento di code coverage funziona inserendo la strumentazione in un assembly immediatamente prima dell'avvio dell'applicazione.  Nell'assembly caricato in precedenza, il codice di inizializzazione in **DllMain** viene eseguito non appena l'assembly viene caricato e prima che l'applicazione venga eseguita.  Il codice risulterà non analizzato.  
  
 In genere, questo si applica agli assembly caricati in modo statico.  
  
 Risoluzione  
 Nessuno.  
  
## Vedere anche  
 [Utilizzo di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)