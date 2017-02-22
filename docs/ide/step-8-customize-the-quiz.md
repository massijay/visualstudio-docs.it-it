---
title: "Passaggio 8: personalizzare il quiz | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Passaggio 8: personalizzare il quiz
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nell'ultima parte dell'esercitazione, è possibile esaminare alcune modalità per personalizzare il quiz e ampliare su ciò che hai già imparato.  Ad esempio, considerare come il programma crea problemi di divisione casuali per cui la risposta non è mai una frazione.  Per esercitarsi ulteriormente, modificare il colore del controllo `timeLabel` e fornire un suggerimento all'utente.  
  
### Personalizzare il layout  
  
-   Quando rimangono solo cinque secondi in un quiz, modificare il colore del controllo **timeLabel** a rosso impostando la proprietà **BackColor** \(`timeLabel.BackColor = Color.Red;`\).  Reimpostare il colore quando il quiz è finito.  
  
-   Fornire un suggerimento all'utente riproducendo un suono quando viene immessa la risposta corretta in un controllo NumericUpDown. \(È necessario scrivere un gestore di evento per l'evento `ValueChanged()` di ogni controllo, che viene attivato ogni qualvolta l'utente modifica il valore del controllo\).  
  
### Per continuare o rivedere l'esercitazione  
  
-   Per scaricare una versione completa del quiz, vedere [Esempio di esercitazione per un quiz matematico completo](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Per passare all'esercitazione successiva, vedere [Esercitazione 3: creare un gioco delle coppie](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Per tornare al passaggio precedente dell'esercitazione, vedere [Passaggio 7: aggiungere problemi di moltiplicazione e divisione](../Topic/Step%207:%20Add%20Multiplication%20and%20Division%20Problems.md).