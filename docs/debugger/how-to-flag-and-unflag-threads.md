---
title: "Procedura: impostare e rimuovere i flag dei thread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "thread, passaggio [debug]"
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura: impostare e rimuovere i flag dei thread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile contrassegnare un thread al quale si desidera prestare particolare attenzione mediante un'icona nella finestra **Thread**, **Stack in parallelo**, **Espressione di controllo in parallelo** e **Thread GPU**.  Questa icona può essere d'aiuto all'utente e ad altri per distinguere i thread con flag dagli altri thread.  
  
 I thread con flag ricevono inoltre un trattamento speciale nell'elenco **Thread** della barra degli strumenti **Posizione di debug**.  In questo elenco possono essere visualizzati tutti i thread o soltanto i thread con flag.  Quando si contrassegna un thread, l'elenco **Thread** passa automaticamente alla visualizzazione dei soli thread con flag, ma è possibile tornare alla visualizzazione di tutti i thread, a seconda delle proprie esigenze.  
  
### Per impostare o rimuovere un flag di un thread utilizzando la finestra Thread  
  
-   Nella finestra **Thread** individuare il thread desiderato e fare clic sull'icona del flag per selezionare o deselezionare il flag.  
  
### Per rimuovere i flag di tutti thread  
  
-   Nella finestra **Thread** fare clic con il pulsante destro del mouse su un thread qualsiasi, quindi scegliere **Rimuovi flag di tutti i thread**.  
  
### Per visualizzare solo i thread con flag  
  
-   Scegliere il pulsante del flag nella finestra di debug.  
  
### Per contrassegnare Just My Code  
  
1.  Fare clic sull'icona del flag nella barra degli strumenti in cima alla finestra **Thread**.  
  
2.  Fare clic su **Contrassegna Just My Code** nell'elenco a discesa.  
  
### Per contrassegnare thread associati ai moduli selezionati  
  
1.  Fare clic sull'icona del flag nella barra degli strumenti della finestra **Thread**.  
  
2.  Fare clic su **Contrassegna selezione moduli personalizzata** nell'elenco a discesa.  
  
3.  Selezionare i moduli desiderati nella finestra di dialogo **Seleziona moduli**.  
  
4.  \(Facoltativo\) Digitare una stringa per cercare moduli specifici nella casella **Cerca**.  
  
5.  Scegliere **OK**.  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md)