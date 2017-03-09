---
title: "Procedura: utilizzare la finestra Disassembly | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.disassembly"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "linguaggio assembly, debug codice assembly inline"
  - "punti di interruzione, finestra Disassembly"
  - "Disassembly (finestra)"
  - "codice macchina"
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare la finestra Disassembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzionalità è disponibile solo se il debug a livello di indirizzo è stato attivato nella finestra di dialogo **Opzioni**, nodo **Debug**.  Non è invece disponibile per il debug di script o SQL.  
  
 Nella finestra **Disassembly** viene visualizzato il codice assembly corrispondente alle istruzioni create dal compilatore.  Se si sta eseguendo il debug di codice gestito, tali istruzioni in linguaggio assembly corrispondono al codice nativo creato dal compilatore JIT \(Just\-In\-Time\), non al linguaggio MSIL \(Microsoft Intermediate Language\) generato dal compilatore di Visual Studio.  
  
 Oltre alle istruzioni in linguaggio assembly, nella finestra **Disassembly** possono essere visualizzate le seguenti informazioni facoltative:  
  
-   L'indirizzo di memoria in cui si trova ciascuna istruzione.  Per applicazioni native, si tratta dell'indirizzo di memoria effettivo.  Per Visual Basic, C\# o codice gestito, si tratta dell'offset dall'inizio della funzione.  
  
-   Codice sorgente dal quale deriva il codice assembly.  
  
-   Byte del codice: rappresentazioni in byte delle effettive istruzioni in linguaggio macchina o MSIL.  
  
-   Nomi di simboli per gli indirizzi di memoria.  
  
-   Numeri di riga corrispondenti al codice sorgente.  
  
 Le istruzioni in linguaggio assembly sono costituite da elementi mnemonici, che sono abbreviazioni di nomi di istruzioni e simboli che rappresentano variabili, registri e costanti.  Ogni istruzione in linguaggio macchina è rappresentata da un elemento mnemonico in linguaggio assembly, seguito in genere da una o più variabili, registri o costanti.  
  
 Se non si è in grado di leggere il linguaggio assembly e si desidera sfruttare appieno i vantaggi della finestra Disassembly, consultare un buon manuale sulla programmazione in linguaggio assembly.  Tale argomento esula dallo scopo di questa breve introduzione alla finestra Disassembly.  
  
 Dal momento che il codice assembly si basa in modo rilevante sui registri del processore o, nel caso di codice gestito, sui registri di Common Language Runtime, sarà particolarmente vantaggioso utilizzare la finestra Disassembly insieme alla finestra Registri, in cui può essere esaminato il contenuto dei registri.  
  
 È poco probabile che si abbia desiderio o necessità di visualizzare istruzioni in linguaggio macchina nel loro formato numerico non elaborato anziché in formato di linguaggio assembly.  Tuttavia, qualora ciò fosse necessario, sarà possibile utilizzare la finestra Memoria o scegliere Mostra byte del codice dal menu di scelta rapida della finestra Disassembly.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per visualizzare la finestra Disassembly  
  
-   Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Disassembly**.  
  
     Il debugger deve essere in esecuzione o in modalità di interruzione.  
  
### Per attivare o disattivare la visualizzazione delle informazioni opzionali  
  
-   Fare clic con il pulsante destro del mouse sulla finestra **Disassembly** e selezionare o deselezionare le opzioni desiderate dal menu di scelta rapida.  
  
     Una freccia gialla sul margine sinistro indica la posizione del punto di esecuzione corrente.  Per il codice nativo la posizione corrisponde al contatore di programma della CPU.  Questo indicatore mostra l'istruzione successiva che verrà eseguita dal programma.  
  
     Per ulteriori informazioni, vedere [Spostamento verso l'alto o verso il basso di una pagina di memoria](../debugger/how-to-page-up-or-down-in-memory.md).  
  
## Vedere anche  
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Procedura: utilizzare la finestra Registri](../debugger/how-to-use-the-registers-window.md)