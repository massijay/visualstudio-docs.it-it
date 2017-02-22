---
title: "Modifica e continuazione (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "C/C++, Modifica e continuazione"
  - "debug [C++], Modifica e continuazione"
  - "Modifica e continuazione [C++]"
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modifica e continuazione (Visual C++)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile usare Modifica e continuazione nei progetti Visual C\+\+. Per informazioni sulle limitazioni di Modifica e continuazione vedere [Modifiche e limitazioni del codice supportato \(C\+\+\)](../debugger/supported-code-changes-cpp.md).  
  
 A partire da Visual Studio 2015 Update 1, è ora possibile usare Modifica e continuazione nelle app C\+\+ di Windows Store e nelle app DirectX, perché è ora supportata l'opzione del compilatore **\/ZI** con l'opzione **\/bigobj**. È anche possibile usare Modifica e continuazione con file binari compilati con l'opzione **\/FASTLINK**.  
  
 Tra gli altri miglioramenti, Update 1 include una nuova finestra di dialogo di attesa annullabile e la notifica quando un file non supporta Modifica e continuazione. Per altre informazioni, vedere l'articolo sui [miglioramenti per Modifica e continuazione di C\+\+ in Visual Studio Update 1](http://blogs.msdn.com/b/vcblog/archive/2015/11/30/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1.aspx).  
  
L'opzione del compilatore [\/Zo \(Enhance Optimized Debugging\)](/visual-cpp/build/reference/zo-enhance-optimized-debugging) introdotta in Visual Studio 2013 Update 3 aggiunge altre informazioni ai file PDB \(di simboli\) per i file binari compilati senza l'opzione [\/Od \(Disable \(Debug\)\)](http://msdn.microsoft.com/library/aafb762y.aspx).  
  
**\/Zo** disabilita Modifica e continuazione. Vedere[Procedura: eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a>Abilitare o disabilitare Modifica e continuazione  
È consigliabile disabilitare la chiamata automatica di Modifica e continuazione se si apportano modifiche al codice che non si vuole applicare durante la sessione di debug corrente. È anche possibile riabilitare la chiamata automatica di Modifica e continuazione.  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** selezionare la cartella **Debug \/ Generale**.  
  
3.  Nel gruppo **Modifica e continuazione** selezionare o deselezionare la casella di controllo **Abilita Modifica e continuazione nativo**.  
  
La modifica di questa impostazione influisce su tutti i progetti attivi. Non è necessario ricompilare l'applicazione dopo la modifica di questa impostazione. L'impostazione può essere modificata anche durante il debug. Quando si compila l'applicazione dalla riga di comando o da un makefile, ma si esegue il debug nell'ambiente Visual Studio, è comunque possibile usare Modifica e continuazione se si imposta l'opzione  **\/ZI**.  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a>Come applicare modifiche al codice in modo esplicito  
In Visual C\+\+, Modifica e continuazione consente di applicare modifiche al codice in due modi: in modo implicito, quando si sceglie un comando di esecuzione, o in modo esplicito, quando si usa il comando **Applica modifiche del codice**.  
  
Quando si applicano modifiche al codice in modo esplicito, il programma rimane in modalità di interruzione e non viene eseguito.  
  
-   Per applicare le modifiche al codice in modo esplicito, nel menu **Debug** scegliere **Applica modifiche del codice**.  
  
## <a name="BKMK_How_to_stop_code_changes"></a>Come interrompere l'applicazione delle modifiche al codice  
In Modifica e continuazione è possibile scegliere di interrompere l'applicazione delle modifiche al codice.  
  
Per interrompere l'applicazione delle modifiche al codice:  
  
-   Nel menu **Debug** scegliere **Interrompi applicazione modifiche del codice**.  
  
Questa voce di menu viene visualizzata solo durante l'applicazione delle modifiche al codice.  
  
Se si sceglie questa opzione, non verrà completata nessuna delle modifiche del codice.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a>Come reimpostare il punto di esecuzione  
Alcune modifiche al codice applicate in modalità Modifica e continuazione possono causare uno spostamento automatico del punto di esecuzione in una nuova posizione. Nonostante il punto di esecuzione venga collocato nel modo più accurato possibile, in alcuni casi il risultato potrebbe non essere corretto.  
  
In Visual C\+\+ la modifica del punto di esecuzione viene segnalata tramite una finestra di dialogo. Si consiglia di verificare che la posizione sia corretta prima di continuare con il debug. In caso negativo, usare il comando **Imposta istruzione successiva**. Per altre informazioni, vedere [Impostare l'istruzione successiva da eseguire](http://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a>Come usare il codice non aggiornato  
In alcuni casi la funzionalità Modifica e continuazione non consente di applicare immediatamente modifiche all'eseguibile, ma può apportare automaticamente tali modifiche in un secondo momento se si continua il debug. Ciò si verifica quando si modifica una funzione che chiama la funzione corrente o si aggiungono più di 64 byte di nuove variabili ad una funzione presente nello stack di chiamate.  
  
In questi casi, il debugger continua a eseguire il codice originale, fino a quando non è possibile applicare le modifiche. Il codice non aggiornato è visualizzato in una finestra del file di origine temporanea di una finestra di origine distinta, caratterizzata da un titolo simile a `enc25.tmp`. L'origine modificata continua ad essere visualizzata nella finestra di origine originale. Se si tenta di modificare il codice non aggiornato, viene visualizzato un messaggio di avviso.  
  
## Vedere anche  
[Modifiche e limitazioni del codice supportato \(C\+\+\)](../debugger/supported-code-changes-cpp.md)