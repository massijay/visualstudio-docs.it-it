---
title: Glossario di Debugger di Visual Studio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- glossary [Debugging SDK]
- debugging [Debugging SDK], glossary
ms.assetid: 4a2cfaab-1fbd-4a23-bd00-9ac4cc50d7fd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d2c34d63b3adb88a588aa84c3d3505db73e817f7
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-debugger-glossary"></a>Glossario di Debugger di Visual Studio
Di seguito sono utilizzati in termini di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK.  
  
## <a name="terms"></a>Termini  
 punto di interruzione associato  
 Un'astrazione per i punti di interruzione impostati nel codice. Esiste una relazione uno a uno tra un punto di interruzione associato e un'istruzione di punto di interruzione nel flusso di codice. Quando il codice viene scaricata, punti di interruzione associati può annullare l'associazione.  
  
 causalità  
 Fornisce la possibilità di tenere traccia di un thread di esecuzione logico tra più thread fisici, processi e le macchine e per ricostruire lo stack di chiamate del thread logico in qualsiasi momento nella durata del thread.  
  
 contesto del codice  
 Fornisce un'astrazione di una posizione nel codice conosciuto al motore di debug. Per la maggior parte delle architetture in fase di esecuzione, un contesto di codice è un indirizzo nel flusso di istruzioni del programma. Per le lingue non convenzionale, in cui codice non può essere rappresentato da istruzioni, un contesto di codice può essere rappresentato con altri mezzi.  
  
 percorso del codice  
 Rappresenta un punto di esecuzione nel codice in cui viene eseguito un ramo o viene effettuata una chiamata di funzione. Una traccia dello stack è essenzialmente un elenco di percorsi di codice della funzione chiamata.  
  
 motore di debug (DE)  
 Un componente che consente il debug di un'architettura in fase di esecuzione. Un motore di debug funziona in combinazione con il sistema operativo o un interprete e fornisce servizi di debug, ad esempio la valutazione di espressione di controllo e i punti di interruzione di esecuzione.  
  
 contesto del documento  
 Fornisce un'astrazione di una posizione in un documento di origine file conosciuto al motore di debug. Per la maggior parte delle lingue, un contesto di documento è una posizione in un file di origine. Per le lingue non convenzionale, per cui il file di origine potrebbe non essere testo, un contesto di documento può essere rappresentato da un altro strumento. Vedere anche *posizione documento*.  
  
 posizione documento  
 Fornisce un'astrazione di una posizione in un file di origine noto all'IDE. Per la maggior parte dei linguaggi, una posizione di documento è una posizione in un file di origine. Per le lingue non convenzionale, una posizione di documento può essere rappresentata in altri modi. Vedere anche *contesto del documento*.  
  
 punto di interruzione di errore  
 Un'astrazione per la descrizione di un errore in un punto di interruzione in sospeso. Un punto di interruzione di errore può descrivere un errore nel percorso del punto di interruzione in sospeso, l'espressione associata con il punto di interruzione in sospeso o altre informazioni che impedisce il punto di interruzione in sospeso dall'associazione in un percorso di codice.  
  
 contesto di valutazione  
 Fornisce un'astrazione di un contesto di programmazione per la valutazione dell'espressione. In genere, un contesto di valutazione è un ambito. Quando si esegue la valutazione di espressioni in un contesto dell'espressione, il contesto di espressione fornisce le regole di ambito che corrispondono il punto di creazione. Ad esempio, il contesto di un'espressione creato in uno stack frame fornirà il contesto per la valutazione di variabili locali, i parametri del metodo, i membri di classe (se applicabile) e variabili globali.  
  
 eccezione intercettata  
 Un'eccezione che viene intercettata da un motore di debug, anche se nessun meccanismo di gestione delle eccezioni sono presente nello stack frame corrente.  
  
 JustMyCode  
 Il concetto di debug solo il codice che appartiene a un utente e ignorare tutto il codice intermedio, ad esempio il codice di sistema, anche se il codice sorgente è disponibile per il codice di sistema.  
  
 punto di interruzione in sospeso  
 Fornisce un'astrazione per i punti di interruzione prima, durante e dopo il codice è caricato e un modo per virtualizzare i punti di interruzione. Un punto di interruzione:  
  
-   Contiene tutte le informazioni necessarie per associare un punto di interruzione al codice in uno o più programmi.  
  
-   Può associare più percorsi di codice in uno o più programmi.  
  
-   Non viene associato al codice.  
  
 Ogni codice in fase di caricamento, vengono controllati tutti i punti di interruzione in sospeso in un programma per verificare se è possibile associare. Un punto di interruzione in sospeso si dice che contiene tutti i punti di interruzione associati che viene associato.  
  
 processo  
 Un processo Win32 fisico. Un processo può contenere più programmi. Vedere anche *programma*.  
  
 programma  
 Un singolo spazio dei nomi in esecuzione all'interno di una particolare architettura in fase di esecuzione. Vedere anche *processo*.  
  
 Gestione sessione di debug (SDM)  
 Gestisce un numero qualsiasi di motori di debug, il debug di un numero qualsiasi di programmi in più processi su un numero illimitato di macchine. A livello di base, il modello SDM è un multiplexer di motori di debug. Inoltre, il modello SDM fornisce una visualizzazione unificata della sessione di debug dell'IDE.  
  
 stack frame  
 Rappresenta lo stato di calcolo su un frame specifico e un livello specifico di chiamate di funzione annidata.  
  
 thread  
 La nozione generalizzata di esecuzione basato su stack istruzione in esecuzione in almeno un programma.  
  
 punto di interruzione di avviso  
 Un'astrazione per la descrizione di un avviso in un punto di interruzione in sospeso. Un punto di interruzione di avviso descrive il motivo per cui il punto di interruzione in sospeso non ancora associato a un percorso di codice. È possibile che il codice non è ancora caricato per il percorso descritto dal punto di interruzione in sospeso o per altri motivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensibilità del Debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
