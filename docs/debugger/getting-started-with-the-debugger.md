---
title: "Introduzione al Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 6
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Introduzione al Debugger
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debugger di Visual Studio è facile da utilizzare in qualsiasi linguaggio.  Di seguito viene illustrato come eseguire il debug di un semplice programma C\#, ma è possibile applicare gli stessi passaggi al codice in altri linguaggi come C\+\+ e JavaScript.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Debug di un progetto C\# di base  
 Si inizia con una semplice applicazione console C\# \(**File \/ Nuovo \/ Progetto**, quindi selezionare **Visual C\#** e quindi **Applicazione console**\).  Se non si è mai lavorato con Visual Studio in precedenza, vedere [Procedura dettagliata: creare un'applicazione semplice](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  Il metodo Main aggiunge semplicemente 1 a una variabile integer 10 volte e stampa il risultato nella console:  
  
```c#  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i < 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Compilare il servizio nella configurazione di **Debug**.  La configurazione è impostata per impostazione predefinita.  Per ulteriori informazioni sulle configurazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
 Eseguire questo codice nel debugger facendo clic su **Debug \/ Avvia debug** \(o su **Avvia** sulla barra degli strumenti oppure premendo F5\).  L’applicazione si chiude quasi immediatamente, pertanto non è possibile affermare se nella finestra della console è stato stampato qualcosa.  
  
 È possibile interrompere l’esecuzione per un tempo sufficiente a visualizzare la finestra Console impostando un punto di interruzione e quindi procedendo.  Per impostare un punto di interruzione, collocare il cursore nella riga `Console.WriteLine` e fare clic su **Debug \/ Nuovo punto di interruzione \/ Punto di interruzione della funzione** oppure fare semplicemente clic nel margine sinistro della stessa riga.  Il punto di interruzione apparirà come segue:  
  
 ![Imposta punto di interruzione](~/docs/debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Per ulteriori informazioni sui punti di interruzione, vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md).  
  
 Avviare di nuovo il debug.  L’esecuzione si interrompe prima dell’esecuzione del codice `Console.WriteLine`.  È possibile causarne l’esecuzione procedendo \(fare clic su **Debug \/ Step Over** o premere **F10**\).  In questo caso scegliendo **Step Into** \(**F11**\) si otterrebbe lo stesso risultato. La differenza sarà spiegata più avanti.  La riga con l’ultima parentesi graffa del metodo dovrebbe essere diventata gialla.  Esaminare la finestra Console.  Dovrebbe apparire **10**.  Interrompere il debug \(**Debug\/Termina debug**,  oppure **Termina debug** sulla barra degli strumenti o **MAIUSC\+F5**\).  
  
 Ora si esaminino i valori delle variabili.  Sotto la finestra del codice si trovano le finestra **Auto**, **Variabili locali** e **Espressioni di controllo**.  Tali finestre mostrano i valori correnti delle variabili al momento dell’esecuzione.  Le finestre **Auto** e **Variabili locali** visualizzano testInt con il valore pari a **10**.  
  
 ![Finestra Auto durante il debug](~/docs/debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Per ulteriori informazioni sulle finestre **Auto** e **Variabili locali**, vedere [Finestre delle variabili](../Topic/Variable%20Windows.md).  
  
 Notare  come cambia il valore di una variabile mentre si esegue il programma.  Impostare un punto di interruzione sulla riga `testInt += 1;` e avviare il debug.  **testInt** nelle finestre **Variabili locali** e **Auto** è **0** e **i** è **1**.  Quando si continua il debug \(**Debug \/ Continua** oppure **Continua** nella barra degli strumenti o **F5**\) si nota che il valore di testInt cambia in **1**, quindi in **2** e così via.  Dopo aver verificato tali modifiche, rimuovere il punto di interruzione \(**Debug \/ Imposta\/Rimuovi punto di interruzione** oppure fare clic  su esso nel margine\) e continuare il debug.  Per rimuovere tutti i punti di interruzione, fare clic su **Debug \/ Elimina tutti i punti di interruzione** oppure premere **CTRL\+SHIFT\+F9** e fare clic su **Sì** nella finestra di dialogo che chiede **Eliminare tutti i punti di interruzione?**.  
  
## Step Into e Step Over nelle chiamate di funzione  
 Per verificare la differenza principale tra **Esegui istruzione** e **Esegui istruzione\/routine**, è necessario aggiungere un metodo chiamato da un altro metodo.  Aggiungere un metodo all’applicazione C\# e chiamarlo dal metodo Main.  Il codice dovrebbe apparire come segue:  
  
```c#  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Impostare un punto di interruzione nella chiamata `Method1();` nel metodo Main e avviare il debug.  Quando si interrompe l'esecuzione, fare clic su **Debug \/ Step Into** \(o **Step Into** sulla barra degli strumenti o **F11**\).  L’esecuzione di interrompe di nuovo alla prima parentesi graffa in Method1\(\):  
  
 ![Esecuzione di istruzioni nel codice](~/docs/debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Interrompere il debug e avviarlo di nuovo, quindi, quando l'esecuzione si arresta al punto di interruzione, fare clic su **Debug\/Step Over**  \(o **Step Over** sulla barra degli strumenti o **F10**\).  L'esecuzione si interrompe nuovamente in `Console.WriteLine("end");`.  
  
 Per ulteriori informazioni sull'esplorazione del codice con il debugger, vedere [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md).