---
title: "Spostarsi nel codice con il Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.execution"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "debug [Visual Studio], controllo di esecuzione"
  - "esecuzione, controllo nel debugger"
  - "esecuzione di istruzioni"
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 42
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spostarsi nel codice con il Debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esistono diversi modi per spostarsi all'interno del codice nel debugger: è possibile passare in o rispetto ai metodi, eseguire fino a un punto di interruzione o un percorso specificato e specificare se si desidera limitare il debug di codice personalizzato o includere simboli per eseguire il debug di codice esterno.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Eseguire istruzione, istruzione\/routine o uscire da istruzione\/routine del codice  
 Una delle più comuni procedure di debug consiste nell'*esecuzione* di una riga di codice alla volta. Quando è stata interrotta l'esecuzione, ad esempio eseguendo il debugger a un punto di interruzione, è possibile usare tre comandi del menu **Debug** per eseguire il codice un'istruzione alla volta:  
  
|Comando di menu|Tasto di scelta rapida|Descrizione|  
|---------------------|----------------------------|-----------------|  
|**Esegui istruzione**|**F11**|Se la riga contiene una chiamata di funzione, scegliendo **Esegui istruzione** verrà eseguita solo la chiamata, quindi il processo si interromperà alla prima riga di codice all'interno della funzione. In caso contrario, scegliendo **Esegui istruzione** verrà eseguita l'istruzione seguente.|  
|**Esegui istruzione\/routine**|**F10**|Se la riga contiene una chiamata di funzione, scegliendo **Esegui istruzione\/routine** verrà eseguita funzione chiamata, quindi il processo si interromperà alla prima riga di codice all'interno della funzione chiamante. In caso contrario, scegliendo **Esegui istruzione** verrà eseguita l'istruzione seguente.|  
|**Esci da istruzione\/routine**|**Shift\+F11**|Scegliendo **Esci da istruzione\/routine**, l'esecuzione del codice verrà ripresa fino a quando la funzione restituirà un risultato e verrà interrotta nel punto di restituzione del risultato all'interno della funzione chiamante.|  
  
-   In una chiamata di funzione annidata, scegliendo **Esegui istruzione** verrà eseguita la funzione annidata più interna. Se si usa **Esegui istruzione** con una chiamata del tipo `Func1(Func2())`, il debugger eseguirà l'istruzione della funzione `Func2`.  
  
-   Il debugger esegue il codice un'istruzione alla volta anziché le righe fisiche. Ad esempio una clausola `if` può essere scritta in una riga:  
  
    ```c#  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```vb  
    Dim x As Integet = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Quando si esegue l'istruzione in questa riga, il debugger esegue la condizione come un unico passaggio e la conseguenza come un altro \(in questo esempio, la condizione è true\).  
  
 Per rilevare visivamente lo stack di chiamate mentre si esegue il codice delle funzioni un'istruzione alla volta, vedere [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Inserire un'interruzione nel codice utilizzando i punti di interruzione oppure Interrompi tutto  
 Durante il debug di un'applicazione con il debugger di VS, l'applicazione può essere in esecuzione oppure in modalità di interruzione.  
  
 L'esecuzione dell'applicazione viene interrotta dal debugger al raggiungimento di un punto di interruzione oppure se si verifica un'eccezione. È comunque possibile interrompere manualmente l'esecuzione in qualsiasi momento.  
  
 Un punto di interruzione è un segnale che indica al debugger di sospendere temporaneamente l'esecuzione dell'applicazione in corrispondenza di un determinato punto. Quando l'esecuzione viene sospesa in corrispondenza di un punto di interruzione, il programma viene detto in modalità di interruzione. L'attivazione della modalità di interruzione non comporta l'arresto né la fine dell'esecuzione del programma; è possibile riprendere l'esecuzione in qualsiasi momento.  
  
 La maggior parte delle funzionalità del debugger, come la visualizzazione dei valori variabili nella finestra Variabili locali o la valutazione delle espressioni nella finestra Espressioni di controllo, sono disponibili unicamente in modalità di interruzione. Tutti gli elementi dell'applicazione restano \(funzioni, variabili e oggetti restano, ad esempio, in memoria\), ma ne vengono sospesi i movimenti e le attività. In modalità di interruzione è possibile esaminare le posizioni e gli stati degli elementi al fine di rilevare violazioni o bug. È anche possibile apportare modifiche all'applicazione in modalità di interruzione  
  
 È possibile configurare i punti di interruzione per sospendere l'esecuzione in base a una serie di condizioni. Vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md). In questa sezione vengono illustrate due operazioni di base per inserire un'interruzione nel codice.  
  
1.  **Impostare punti di interruzione nel codice**  
  
     Per impostare un punto di interruzione semplice nel codice, aprire il file di origine nell'editor di Visual Studio. Impostare il cursore sulla riga di codice che si desidera interrompere, quindi scegliere **Punto di interruzione**, **Inserisci punto di interruzione** dal menu di scelta rapida \(tastiera: **F9**\). Il debugger interrompe l'esecuzione subito prima che la riga venga eseguita.  
  
     ![Imposta punto di interruzione](~/debugger/media/dbg_basics_setbreakpoint.png "DBG\_Basics\_SetBreakpoint")  
  
     I punti di interruzione in Visual Studio forniscono un'ampia gamma di funzionalità aggiuntive, ad esempio punti di interruzione e punti di analisi condizionali. Vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md).  
  
2.  **Inserire un'interruzione nel codice manualmente**  
  
     Per inserire un'interruzione nella successiva riga di codice disponibile in un'applicazione in esecuzione, scegliere **Debug**, **Interrompi tutto** \(tastiera: **Ctrl\+Alt\+Break**\).  
  
-   Se si esegue il debug con l'opzione Just My Code attivata, si interrompe alla riga di codice successiva nel progetto. Vedere [Limitare l'esecuzione di istruzioni a Just My Code](#BKMK_Restrict_stepping_to_Just_My_Code).  
  
-   Se si sta eseguendo il debug di più programmi, per impostazione predefinita l'utilizzo del comando Interrompi tutto o di un punto di interruzione avrà effetto su tutti i programmi in corso di debug. Vedere [Configurare il comportamento di esecuzione di più processi](../debugger/debug-multiple-processes.md#BKMK_Configure_the_execution_behavior_of_multiple_processes).  
  
-   Se si interrompe l'esecuzione del codice senza file \(con estensione pdb\) di simboli o di origine corrispondenti, il debugger visualizza una pagina **File di origine non trovati** o **Simboli non trovati** che consente di trovare i file appropriati. Vedere [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
     Se non è possibile accedere ai file di supporto, è comunque possibile eseguire il debug delle istruzioni di assembly nella finestra Disassembly.  
  
##  <a name="BKMK_Run_to_a_specified_location_or_function"></a> Eseguire fino a una funzione o un percorso specificato.  
 A volte può essere necessario eseguire il programma solo fino a un determinato punto del codice, quindi interromperne l'esecuzione. Se in tale posizione è stato impostato un punto di interruzione, scegliere **Debug**, **Avvia debug** se non è stato avviato il debug, o **Debug**, **Continua**. In entrambi i casi **F5** è il tasto di scelta rapida. Il debugger si arresta in corrispondenza del punto di interruzione successivo nell'esecuzione del codice. Scegliere **Debug**, **Continua** fino a raggiungere il punto di interruzione desiderato.  
  
 È inoltre possibile eseguire fino alla pozione del cursore nell'editor di codice o eseguire la funzione specificata.  
  
 **Eseguire fino alla posizione del cursore.**  
  
 Per eseguire fino alla posizione del cursore, posizionare il cursore su una riga di codice eseguibile in una finestra di origine. Nel menu di scelta rapida dell'editor, scegliere **Esegui fino al cursore**.  
  
 **Eseguire fino a una funzione nello stack di chiamate**  
  
 Nella finestra **Stack di chiamate** selezionare la funzione e scegliere **Esegui fino al cursore** dal menu di scelta rapida. Per rilevare visivamente lo stack di chiamate, vedere [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
 **Eseguire fino a una funzione specificata mediante il nome**  
  
 È possibile indicare al debugger di eseguire l'applicazione fino al raggiungimento di una funzione specificata. È possibile specificare la funzione mediante il nome oppure sceglierla dallo stack di chiamate.  
  
 Per specificare una funzione mediante il nome, scegliere **Debug**, **Nuovo punto di interruzione**, **Interrompi alla funzione**, quindi immettere il nome della funzione e altre informazioni di identificazione.  
  
 ![Finestra di dialogo Nuovo punto di interruzione](../debugger/media/dbg_execution_newbreakpoint.png "DBG\_Execution\_NewBreakpoint")  
  
 Se la funzione è sottoposta a overload o è disponibile nello spazio dei nomi, è possibile scegliere le funzioni desiderate nella finestra di dialogo **Seleziona punti di interruzione**.  
  
 ![Finestra di dialogo Seleziona punti di interruzione](~/debugger/media/dbg_execution_overloadedbreakpoints.png "DBG\_Execution\_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Impostare l'istruzione successiva da eseguire  
 Dopo aver inserito un'interruzione nel debugger è possibile spostare il punto di esecuzione per impostare la successiva istruzione di codice da eseguire. La posizione dell'istruzione successiva da eseguire è contrassegnata da una freccia gialla visualizzata sul margine di una finestra di origine o di una finestra Disassembly. Mediante lo spostamento della freccia, è possibile ignorare un segmento di codice oppure tornare a una riga eseguita precedentemente. È possibile usare questa opzione in alcune situazioni, ad esempio quando si desidera ignorare una sezione di codice che contiene un bug noto.  
  
 ![Example2](~/debugger/media/dbg_basics_example2.png "DBG\_Basics\_Example2")  
  
 Per impostare l'istruzione successiva da eseguire, utilizzare una di queste procedure:  
  
-   In una finestra di origine trascinare la freccia gialla nella posizione in cui si desidera impostare l'istruzione successiva all'interno dello stesso file di origine.  
  
-   Nella finestra di origine impostare il cursore sulla riga da eseguire successivamente e scegliere **Imposta istruzione successiva** nel menu di scelta rapida.  
  
-   Nella finestra Disassembly impostare il cursore sull'istruzione dell'assembly che si vuole eseguire successivamente e scegliere **Imposta istruzione successiva** nel menu di scelta rapida.  
  
> [!CAUTION]
>  Quando si imposta l'istruzione successiva, il contatore del programma passa direttamente alla nuova posizione. Usare questo comando con cautela:  
>   
>  -   Le istruzioni comprese tra il vecchio e il nuovo punto di esecuzione non verranno eseguite.  
> -   Se si sposta all'indietro il punto di esecuzione, le istruzioni comprese tra questo e il vecchio punto di interruzione non verranno annullate.  
> -   Lo spostamento dell'istruzione successiva in corrispondenza di un'altra funzione o ambito provoca in genere un errore dello stack di chiamate e, conseguentemente, un errore o un'eccezione di runtime. Se si sposta l'istruzione successiva in corrispondenza di un altro ambito, verrà visualizzata una finestra di dialogo contenente un avviso e in cui si può scegliere di annullare l'operazione. In Visual Basic non è possibile spostare l'istruzione successiva in corrispondenza di un altro ambito o di un'altra funzione.  
> -   Se in C\+\+ nativo sono abilitati i controlli runtime, l'impostazione dell'istruzione successiva può causare la generazione di un'eccezione quando l'esecuzione raggiunge la fine del metodo.  
> -   Quando l'opzione Modifica e continuazione è abilitata, **Imposta istruzione successiva** avrà esito negativo se sono state effettuate modifiche per cui Modifica e continuazione non è immediatamente in grado di eseguire nuovamente il mapping. Ad esempio questo può accadere se è stato modificato del codice all'interno di un blocco catch. Quando succede, verrà visualizzato un messaggio di errore indicante che l'operazione non è supportata.  
  
> [!NOTE]
>  Nel codice gestito non è possibile spostare l'istruzione successiva in presenza delle seguenti condizioni:  
>   
>  -   L'istruzione successiva è inclusa in un metodo diverso da quello dell'istruzione corrente.  
> -   Il debug è stato avviato utilizzando il debug JIT.  
> -   È in corso la rimozione di uno stack di chiamate.  
> -   È stata generata un'eccezione System.StackOverflowException or System.Threading.ThreadAbortException.  
  
 Non è possibile impostare l'istruzione successiva mentre l'applicazione è in esecuzione. Per impostare l'istruzione successiva, è necessario che il debugger sia in modalità di interruzione.  
  
##  <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a> Limitare l'esecuzione di istruzioni a Just My Code  
 In alcuni casi è possibile che, durante il debug, si desideri vedere solo il codice scritto personalmente e ignorarne altro, come le chiamate di sistema. Questa operazione può essere eseguita con il debug Just My Code, che nasconde il codice non utente in modo che non sia presente nelle finestre del debugger. Durante l'esecuzione, il debugger scorre, un'istruzione alla volta, il codice non utente, ma non si arresta. Vedere [Just My Code](../debugger/just-my-code.md)  
  
> [!NOTE]
>  Just My Code non è supportato per progetti per dispositivi.  
  
##  <a name="BKMK_Step_into_system_calls"></a> Eseguire le chiamate di sistema  
 Se sono stati caricati simboli di debug per il codice di sistema e Just My Code non è abilitato, è possibile eseguire le istruzioni di una chiamata di sistema come una qualsiasi altra chiamata.  
  
 Per accedere ai file di simboli Microsoft, vedere [Usare i server di simboli per trovare i file di simboli che non sono presenti nel computer locale](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) nell'argomento [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Per caricare i simboli per un componente di sistema specifico durante il debug:  
  
1.  Aprire la finestra Moduli \(tastiera: **Ctrl\+Alt\+U**\).  
  
2.  Selezionare il modulo per cui si desidera caricare i simboli.  
  
     I moduli con i simboli caricati sono presenti nella colonna **Stato simboli**.  
  
3.  Scegliere **Carica simboli** dal menu di scelta rapida.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Eseguire istruzioni di proprietà e operatori nel codice gestito  
 Il debugger esegue le istruzioni\/routine di proprietà e operatori nel codice gestito per impostazione predefinita. Nella maggior parte dei casi, l'esperienza di debug risulta notevolmente migliorata. Per abilitare l'esecuzione di istruzioni di proprietà o operatori, scegliere **Debug**, **Opzioni e impostazioni**. Nella pagina **Debug**, **Generale** deselezionare la casella di controllo **Esegui istruzione\/routine di proprietà e operatori \(solo gestito\)**