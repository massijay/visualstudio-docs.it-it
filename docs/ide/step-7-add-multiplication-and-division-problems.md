---
title: 'Passaggio 7: aggiungere problemi di moltiplicazione e divisione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 17
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 481d1ad8050a0b028a7cbf23f9385c9920feb1a2
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="step-7-add-multiplication-and-division-problems"></a>Passaggio 7: aggiungere problemi di moltiplicazione e divisione
Nella settima parte di questa esercitazione si aggiungeranno i problemi di moltiplicazione e divisione, ma prima di procedere vedere come effettuare questa modifica. Considerare il passaggio iniziale, che comporta l'archiviazione dei valori.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Per aggiungere problemi di moltiplicazione e divisione  
  
1.  Aggiungere altre quattro variabili di tipo Integer al modulo.  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]  [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  Come in precedenza, modificare il metodo `StartTheQuiz()` per inserire numeri casuali per i problemi di moltiplicazione e divisione.  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]  [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  Modificare il metodo `CheckTheAnswer()` in modo che controlli anche i problemi di moltiplicazione e divisione.  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]  [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     Poiché non esiste un modo semplice di immettere il segno di moltiplicazione (×) e il segno di divisione (÷) utilizzando la tastiera, in Visual C# e Visual Basic si utilizza un asterisco (*) per la moltiplicazione e una barra (/) per la divisione.  
  
4.  Modificare l'ultima parte del gestore dell'evento Tick del timer in modo che inserisca la risposta corretta alla scadenza del tempo.  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]  [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  Salvare ed eseguire il programma.  
  
     Gli esecutori del quiz devono risolvere quattro problemi per completare il quiz, come illustrato di seguito.  
  
     ![Quiz matematico con quattro problemi](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Quiz matematico con quattro problemi  
  
### <a name="to-continue-or-review"></a>Per continuare o rivedere l'esercitazione  
  
-   Per andare al passaggio successivo dell'esercitazione, vedere [Passaggio 8: personalizzare il quiz](../ide/step-8-customize-the-quiz.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 6: aggiungere un problema di sottrazione](../ide/step-6-add-a-subtraction-problem.md).
