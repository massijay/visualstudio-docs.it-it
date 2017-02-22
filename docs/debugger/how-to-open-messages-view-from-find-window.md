---
title: "Procedura: aprire la visualizzazione messaggi dalla finestra Trova | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visualizzazione messaggi in Spy++, apertura"
  - "apertura della visualizzazione messaggi in Spy++"
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: aprire la visualizzazione messaggi dalla finestra Trova
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Può essere opportuno per l'utente utilizzare la finestra di dialogo **Trova finestra** per selezionare una finestra di destinazione e aprire quindi una visualizzazione messaggi di tale finestra.  
  
### Per aprire una visualizzazione messaggi tramite la finestra di dialogo Trova finestra  
  
1.  Disporre le finestre in modo che la finestra di Spy\+\+ e quella di destinazione siano visibili.  
  
2.  Scegliere **Trova finestra** dal menu **Spy**.  
  
     Viene visualizzata la [finestra di dialogo Trova finestra](../debugger/find-window-dialog-box.md).  
  
3.  Trascinare lo **strumento di ricerca** dalla scheda **Finestre** sulla finestra di destinazione.  Quando si trascina lo strumento, nella finestra di dialogo **Trova finestra** vengono visualizzati i dettagli sulla finestra selezionata.  
  
     \- oppure \-  
  
     Se si conosce l'handle della finestra che si desidera esaminare \(copiato ad esempio dal debugger\), è possibile digitarlo nella casella di testo **Handle**.  
  
4.  Selezionare **Messaggi** in **Mostra**.  
  
5.  Scegliere **OK**.  
  
     Viene aperta una finestra [Visualizzazione messaggi](../debugger/messages-view.md) vuota e aggiunto un menu **Messaggi** alla barra degli strumenti di Spy\+\+.  
  
6.  Scegliere **Opzioni di registrazione** dal menu **Messaggi**.  
  
     Viene visualizzata la [finestra di dialogo Opzioni messaggio](../debugger/message-options-dialog-box.md).  
  
7.  Selezionare le opzioni per i messaggi che si desidera visualizzare.  
  
8.  Premere **OK** per iniziare la registrazione dei messaggi.  
  
     In base alle opzioni selezionate, i messaggi cominciano a essere inviati in un flusso nella finestra di visualizzazione messaggi attiva.  
  
9. Quando si raggiunge un numero sufficiente di messaggi, scegliere **Arresta registrazione** dal menu **Messaggi**.