---
title: "Passaggio 6: aggiungere un problema di sottrazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Passaggio 6: aggiungere un problema di sottrazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella sesta parte di questa esercitazione si aggiungerà un problema di sottrazione e si apprenderà come eseguire le attività seguenti:  
  
-   Archiviare i valori della sottrazione.  
  
-   Generare numeri casuali per il problema e verificare che la risposta sia compresa tra 0 e 100.  
  
-   Aggiornare il metodo che controlla le risposte in modo che verifichi anche il nuovo problema di sottrazione.  
  
-   Aggiornare il gestore dell'evento Tick del timer in modo che fornisca la risposta corretta quando il tempo scade.  
  
### Per aggiungere un problema di sottrazione  
  
1.  Aggiungere al form due variabili Integer per il problema di sottrazione, tra le variabili Integer per il problema di addizione e il timer.  Il codice dovrebbe essere analogo al seguente.  
  
     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-cs[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]  
  
     I nomi delle nuove variabili Integer, **minuendo** e **sottraendo**, non sono termini di programmazione.  Si tratta dei nomi tradizionali in aritmetica per il numero che si sta sottraendo \(il sottraendo\) e il numero da cui si sottrae \(il minuendo\).  La differenza è il minuendo meno il sottraendo.  È possibile utilizzare altri nomi, perché il programma non richiede nomi specifici per variabili, controlli, componenti o metodi.  È necessario attenersi alle regole, ad esempio i nomi non devono iniziare con una cifra, ma è in genere possibile utilizzare nomi quali x1, x2, x3 e x4.  Tuttavia, i nomi generici rendono il codice difficile da leggere e complicano il rilevamento dei problemi.  Per avere nomi di variabili univoci e significativi, utilizzare i nomi tradizionali per la moltiplicazione \(moltiplicando × moltiplicatore \= prodotto\) e la divisione \(dividendo ÷ divisore \= quoziente\).  
  
     A questo punto, verrà modificato il metodo `StartTheQuiz()` per fornire valori casuali per il problema di sottrazione.  
  
2.  Aggiungere il codice seguente dopo il commento "Completare il problema di sottrazione".  
  
     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-cs[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]  
  
     Per evitare risposte negative per il problema di sottrazione, nel codice il metodo `Next()` della classe `Random` viene utilizzato in modo diverso rispetto al problema di addizione.  Quando si assegnano due valori al metodo `Next()`, viene scelto un numero casuale maggiore o uguale al primo valore e minore del secondo.  Nel codice seguente viene scelto un numero casuale da 1 a 100, che viene archiviato nella variabile minuendo.  
  
     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-cs[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]  
  
     È possibile chiamare in più modi il metodo `Next()` della classe `Random`, denominato "randomizer" in questa esercitazione.  I metodi che è possibile chiamare in più modi sono denominati metodi di overload ed è possibile utilizzare IntelliSense per esplorarli.  Esaminare nuovamente la descrizione comando della finestra di IntelliSense per il metodo `Next()`.  
  
     ![Descrizione comando della finestra di IntelliSense](~/ide/media/express_overloads.png "Express\_Overloads")  
Descrizione comando della finestra di IntelliSense  
  
     La dicitura **\(\+ 2 overload\)** della descrizione comando indica che è possibile chiamare il metodo `Next()` in altri due modi.  Gli overload contengono numeri o tipi di argomenti diversi, pertanto funzionano in modo leggermente diverso l'uno dall'altro.  Ad esempio, un metodo potrebbe accettare un argomento Integer singolo, mentre uno degli overload potrebbe accettare un Integer e una stringa.  Scegliere l'overload corretto in base all'operazione da eseguire.  Quando si aggiunge codice al metodo `StartTheQuiz()`, nella finestra di Intellisense vengono visualizzate più informazioni non appena si immette `randomizer.Next(`.  Premere i tasti freccia SU e GIÙ per scorrere gli overload, come illustrato nell'immagine seguente.  
  
     ![Overload per il metodo Next&#40;&#41; in IntelliSense](~/ide/media/express_nextoverload.png "Express\_NextOverload")  
Overload per il metodo Next\(\) in IntelliSense  
  
     In questo caso, si desidera scegliere l'ultimo overload, perché consente di specificare i valori minimo e massimo.  
  
3.  Modificare il metodo `CheckTheAnswer()` per verificare la risposta corretta per la sottrazione.  
  
     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-cs[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]  
  
     In Visual C\# `&&` corrisponde all'operatore `logical and`.  In Visual Basic l'operatore equivalente è `AndAlso`.  Questi operatori indicano "Se la somma di addendo1 e addendo2 è uguale al valore NumericUpDown della somma e se minuendo meno sottraendo è uguale al valore NumericUpDown della differenza". Il metodo `CheckTheAnswer()` restituisce `true` solo se le risposte ai problemi dell'addizione e della sottrazione sono corrette.  
  
4.  Sostituire l'ultima parte del gestore eventi Tick del timer con il codice seguente in modo che inserisca la risposta corretta alla scadenza del tempo.  
  
     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-cs[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]  
  
5.  Salvare ed eseguire il codice.  
  
     Il programma include un problema di sottrazione, come illustrato nella figura seguente.  
  
     ![Quiz matematico con sottrazione](../ide/media/express_addsubtract.png "Express\_AddSubtract")  
Quiz matematico con problema di sottrazione  
  
### Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 7: aggiungere problemi di moltiplicazione e divisione](../Topic/Step%207:%20Add%20Multiplication%20and%20Division%20Problems.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 5: aggiungere gestori di eventi Enter per i controlli NumericUpDown](../Topic/Step%205:%20Add%20Enter%20Event%20Handlers%20for%20the%20NumericUpDown%20Controls.md).