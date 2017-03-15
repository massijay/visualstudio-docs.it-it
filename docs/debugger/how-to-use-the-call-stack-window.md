---
title: "Procedura: utilizzare la finestra Stack di chiamate | Microsoft Docs"
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
  - "vs.debug.callstack"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "aspx"
helpviewer_keywords: 
  - "threading [Visual Studio], visualizzazione chiamate a o da"
  - "funzioni [debugger], visualizzazione codice su stack di chiamate"
  - "codice disassembly"
  - "punti di interruzione, finestra Stack di chiamate"
  - "debug [Visual Studio], passaggio a un altro stack frame"
  - "debug [Visual Studio], finestra Stack di chiamate"
  - "Finestra Stack di chiamate, visualizzazione del codice sorgente per le funzioni sullo stack di chiamate"
  - "stack, passaggio da uno stack frame all'altro"
  - "Finestra Stack di chiamate, visualizzazione del codice disassembly per le funzioni sullo stack di chiamate"
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: utilizzare la finestra Stack di chiamate
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Tramite la finestra **Stack di chiamate** è possibile visualizzare le chiamate di funzione o di routine attualmente presenti nello stack.  
  
 Nella finestra **Stack di chiamate** vengono visualizzati il nome di ogni funzione e il linguaggio di programmazione nel quale è scritta.  Il nome della funzione o della procedura può essere seguito da informazioni facoltative quali il nome del modulo, il numero di riga, oltre a nomi, tipi e valori di parametri.  La visualizzazione di queste informazioni opzionali può essere attivata o disattivata.  
  
 Lo stack frame in cui è attualmente posizionato il puntatore di esecuzione è contraddistinto da una freccia gialla.  Per impostazione predefinita, si tratta del frame le cui informazioni vengono visualizzate nella finestra di origine, nonché nelle finestre **Disassembly**, **Variabili locali**, **Espressioni di controllo** e **Auto**.  Se lo si desidera, è possibile modificare il contesto specificando un altro frame dello stack nella finestra **Stack di chiamate**.  
  
 Quando i simboli per il debug non sono disponibili per una parte di uno stack di chiamate, è possibile che nella finestra **Stack di chiamate** non vengano visualizzate informazioni corrette per tale parte.  Verrà visualizzata la notazione seguente:  
  
 \[I frame indicati di seguito possono essere errati e\/o mancanti, non sono stati caricati simboli per nome.dll\]  
  
 Nel codice gestito, per impostazione predefinita la finestra **Stack di chiamate** nasconde informazioni per codice non utente.  Di seguito è riportata la notazione visualizzata in sostituzione delle informazioni nascoste:  
  
 **\[\<External Code\>\]**  
  
 Per codice non utente si intende qualsiasi codice diverso da "My Code". Per visualizzare le informazioni sullo stack di chiamate per il codice non utente, utilizzare il menu di scelta rapida.  
  
 Utilizzando il menu di scelta rapida, è possibile scegliere se visualizzare o meno le chiamate tra thread.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso.  Per modificare le impostazioni, selezionare **Importa\/Esporta impostazioni** nel menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per visualizzare la finestra Stack di chiamate in modalità di interruzione o di esecuzione  
  
-   Selezionare **Finestre** dal menu **Debug**, quindi fare clic su **Stack di chiamate**.  
  
### Per scegliere quali informazioni opzionali visualizzare  
  
-   Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e impostare o deselezionare **Mostra \<***the information that you want***\>**.  
  
### Per visualizzare i frame del codice non utente nella finestra Stack di chiamate  
  
-   Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Mostra codice esterno**.  
  
### Per passare a un altro stack frame  
  
1.  Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sul frame di cui si desidera visualizzare codice e dati.  
  
2.  Selezionare **Passa al frame**.  
  
     Accanto al frame selezionato verrà visualizzata una freccia verde ricurva.  Il puntatore di esecuzione rimarrà nel frame originale, sempre contrassegnato dalla freccia gialla.  Se si sceglie **Esegui** o **Continua** dal menu **Debug**, l'esecuzione continuerà nel frame originale, non nel frame selezionato.  
  
### Per visualizzare le chiamate da o verso altri thread  
  
-   Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Includi chiamate da e verso altri thread**.  
  
### Per visualizzare il codice sorgente di una funzione dello stack di chiamate  
  
-   Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si desidera esaminare il codice sorgente e selezionare **Vai a codice sorgente**.  
  
### Per rilevare visivamente lo stack di chiamate  
  
1.  Nella finestra **Stack di chiamate** aprire il menu di scelta rapida.  Scegliere **Mostra stack di chiamate sulla mappa codici**. \(Tastiera: **CTRL** \+ **MAIUSC** \+ **\`**\)  
  
     Vedere [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### Per visualizzare il codice disassembly di una funzione dello stack di chiamate  
  
-   Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si desidera esaminare il codice del disassembly e selezionare **Vai a disassembly**.  
  
### Per eseguire una funzione specifica dalla finestra Stack di chiamate  
  
-   Vedere [Eseguire fino a una funzione o un percorso specificato.](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Run_to_a_specified_location_or_function).  
  
### Per impostare un punto di interruzione in corrispondenza del punto di uscita di una chiamata di funzione  
  
-   Vedere [Impostare un punto di interruzione in corrispondenza di una riga di codice sorgente, un'istruzione di assembly o una funzione dello stack di chiamate](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_at_a_source_line__assembly_instruction__or_call_stack_function_)  
  
### Per caricare i simboli per un modulo  
  
-   Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sul frame in cui viene visualizzato il modulo contenente i simboli che si desidera ricaricare e selezionare **Carica simboli**.  
  
## Caricamento dei simboli  
 Nella finestra **Stack di chiamate** è possibile caricare i simboli di debug per un codice che non ne dispone.  Questi simboli possono essere simboli di sistema o .NET Framework scaricati dai server dei simboli pubblici Microsoft o simboli contenuti in un percorso nel computer del quale si esegue il debug.  
  
 Vedere [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### Per caricare i simboli  
  
1.  Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sul frame per il quale non sono caricati i simboli.  Il frame verrà disattivato \(rappresentato in grigio\).  
  
2.  Scegliere **Carica simboli da**, quindi fare clic su **Server dei simboli Microsoft** o **Percorso simboli**.  
  
#### Per impostare il percorso dei simboli  
  
1.  Nella finestra **Stack di chiamate** scegliere **Impostazioni simboli** nel menu di scelta rapida.  
  
     Viene visualizzata la finestra di dialogo **Opzioni** con la pagina **Simboli**.  
  
2.  Fare clic su **Impostazioni simboli**.  
  
3.  Nella finestra di dialogo **Opzioni** fare clic sull'icona della cartella.  
  
     Viene visualizzato un cursore nella casella **Percorsi dei file di simboli \(pdb\)**.  
  
4.  Digitare il percorso di directory del simbolo sul computer del quale si esegue il debug.  Per il debug locale, è il computer locale.  Per il debug remoto, è il computer remoto.  
  
5.  Scegliere **OK** per chiudere la finestra di dialogo **Opzioni**.  
  
## Vedere anche  
 [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Procedura: modificare il formato numerico delle finestre del debugger](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)