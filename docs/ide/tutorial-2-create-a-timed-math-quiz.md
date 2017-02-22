---
title: "Esercitazione 2: creare un quiz matematico a tempo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Esercitazione 2: creare un quiz matematico a tempo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa esercitazione si compila un quiz dove l'esecutore deve rispondere a quattro problemi aritmetici casuali entro il tempo specificato.  Vengono illustrate le seguenti procedure:  
  
-   Generare numeri casuali utilizzando la classe `Random`.  
  
-   Attivare eventi che devono verificarsi in un momento specifico utilizzando un controllo **Timer**.  
  
-   Controllare il flusso di programma mediante istruzioni `if else`.  
  
-   Eseguire operazioni aritmetiche di base nel codice.  
  
 Al termine, il quiz sarà simile all'immagine riportata di seguito, ma con numeri diversi.  
  
 ![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png "Express\_FinishedQuiz")  
Quiz creato in questa esercitazione  
  
 Per scaricare una versione completa del quiz, vedere [Esempio di esercitazione per un quiz matematico completo](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
>  In questa esercitazione sono trattati sia Visual C\# sia Visual Basic; concentrarsi sulle informazioni specifiche del linguaggio di programmazione in uso.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Passaggio 1: creare un progetto e aggiungere etichette al form](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Iniziare creando il progetto, modificando le proprietà e aggiungendo controlli `Label`.|  
|[Passaggio 2: creare un problema di addizione casuale](../ide/step-2-create-a-random-addition-problem.md)|Creare un problema di addizione e utilizzare la classe `Random` per generare numeri casuali.|  
|[Passaggio 3: aggiungere un timer per il conto alla rovescia](../Topic/Step%203:%20Add%20a%20Countdown%20Timer.md)|Aggiungere un timer per il conto alla rovescia in modo che sia possibile impostare una durata per il quiz.|  
|[Passaggio 4: aggiungere il metodo CheckTheAnswer\(\)](../Topic/Step%204:%20Add%20the%20CheckTheAnswer\(\)%20Method.md)|Aggiungere un metodo per controllare se l'esecutore del quiz ha immesso una risposta corretta al problema.|  
|[Passaggio 5: aggiungere gestori di eventi Enter per i controlli NumericUpDown](../Topic/Step%205:%20Add%20Enter%20Event%20Handlers%20for%20the%20NumericUpDown%20Controls.md)|Aggiungere gestori eventi per semplificare lo svolgimento del quiz.|  
|[Passaggio 6: aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md)|Aggiungere un problema di sottrazione che genera numeri casuali, utilizza il timer e controlla le risposte corrette.|  
|[Passaggio 7: aggiungere problemi di moltiplicazione e divisione](../Topic/Step%207:%20Add%20Multiplication%20and%20Division%20Problems.md)|Aggiungere problemi di moltiplicazione e divisione che generano numeri casuali, utilizzano il timer e controllano le risposte corrette.|  
|[Passaggio 8: personalizzare il quiz](../ide/step-8-customize-the-quiz.md)|Provare altre funzionalità, ad esempio la modifica dei colori e l'aggiunta di un suggerimento.|