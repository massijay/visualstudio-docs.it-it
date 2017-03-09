---
title: "Procedura: modificare il computer di riproduzione della diagnostica grafica | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: modificare il computer di riproduzione della diagnostica grafica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile riprodurre le informazioni grafiche tramite il computer locale, o tramite un computer remoto o un dispositivo.  
  
## Scegliere un computer di riproduzione  
 Il computer di riproduzione è un computer o un dispositivo utilizzato per riprodurre gli eventi di grafica da un log di grafica.  In genere, il computer locale è la soluzione più semplice, ma un problema di rendering non potrebbe riprodursi in un computer con hardware o versioni di driver diverse dalla versione del computer in cui è stato acquisito; in questo caso, è possibile scegliere un computer riproduzione remoto che riproduce meglio il problema e utilizzare comunque il computer di sviluppo per diagnosticarlo.  
  
#### Per utilizzare il computer locale per riprodurre informazioni grafiche  
  
1.  Nella finestra di documenti Log di grafica scegliere il collegamento **Computer riproduzione**.  Verrà visualizzata la finestra di dialogo **Connessioni per il debugger remoto**.  
  
2.  In **Configurazione manuale**, nella proprietà **Indirizzo**, immettere `localhost`.  
  
3.  Impostare la proprietà **Modalità di autenticazione** su **Nessuna**.  
  
4.  Fare clic sul pulsante **Seleziona**.  
  
#### Per utilizzare un computer remoto per riprodurre informazioni grafiche  
  
1.  Nella finestra di documenti Log di grafica scegliere il collegamento **Computer riproduzione**.  Verrà visualizzata la finestra di dialogo **Connessioni per il debugger remoto**.  
  
2.  In **Configurazione manuale**, nella proprietà **Indirizzo**, immettere il nome di dominio Windows o l'indirizzo IP del computer o del dispositivo che si desidera utilizzare per riprodurre le informazioni grafiche.  
  
3.  Specificare il tipo di autorizzazione che si desidera utilizzare per assicurare la connessione al computer di riproduzione.  
  
    -   Per l'autenticazione di Windows, impostare la proprietà **Modalità di autenticazione** su **Windows**.  
  
    -   In caso di nessuna autenticazione, impostare la proprietà **Modalità di autenticazione** su **Nessuna**.  
  
4.  Fare clic sul pulsante **Seleziona**.  
  
> [!NOTE]
>  La finestra di dialogo **Connessioni del debugger remoto** potrebbe visualizzare le destinazioni di debug remoto che sono connesse direttamente al computer di sviluppo o che si trovano nella stessa subnet.  È possibile utilizzare una di queste destinazioni di debug remoto nel computer della riproduzione di diagnostica grafiche senza configurarlo manualmente.  Nella finestra di dialogo **Connessioni debugger remoto** selezionare la destinazione desiderata, quindi scegliere il pulsante **Seleziona**.  
  
## Vedere anche  
 [Documento log grafica](../debugger/graphics-log-document.md)