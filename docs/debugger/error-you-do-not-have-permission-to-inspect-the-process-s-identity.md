---
title: "Errore: Non si dispone dell&#39;autorizzazione necessaria per controllare l&#39;identit&#224; del processo | Microsoft Docs"
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
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: Non si dispone dell&#39;autorizzazione necessaria per controllare l&#39;identit&#224; del processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Non si dispone dell'autorizzazione necessaria per controllare l'identità del processo.Probabilmente l'errore è causato dalla configurazione del sistema.  
  
 Il debugger non è stato in grado di controllare l'identità del processo, un'informazione necessaria per l'esecuzione del debug.  Probabilmente Servizi terminal è disabilitato.  Per impostazione predefinita, questo servizio è attivato.  Per riattivarlo, eseguire la procedura seguente.  
  
### Per attivare Servizi terminal  
  
1.  Fare clic su **Start**, quindi scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo scegliere **Passa alla visualizzazione classica**, se necessario, quindi fare doppio clic su **Strumenti di amministrazione**.  
  
3.  Nella finestra **Strumenti di amministrazione** fare doppio clic su **Gestione computer**.  
  
4.  Nella finestra di Gestione computer espandere il nodo **Servizi e applicazioni**.  
  
5.  In **Servizi e applicazioni** fare clic su **Servizi**.  
  
     Nel riquadro di destra verrà visualizzato un elenco di servizi.  
  
6.  Nell'elenco **Servizi** fare clic con il pulsante destro del mouse su **Servizi terminal** e quindi scegliere **Proprietà**.  
  
7.  Nella finestra **Proprietà Servizi terminal** passare alla scheda **Generale** e impostare **Tipo di avvio** su **Manuale**.  
  
8.  Scegliere **OK**.  
  
9. Riavviare il computer.  
  
     Con questa procedura non si attiva automaticamente Desktop remoto.  Se si desidera attivare Desktop remoto nel computer in uso, eseguire la procedura aggiuntiva seguente.  
  
### Per attivare Desktop remoto  
  
1.  Fare clic su **Start** e quindi fare clic con il pulsante destro del mouse su **Risorse del computer**.  
  
2.  Scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra **Proprietà del sistema**.  
  
3.  Fare clic su **Connessione remota**.  
  
4.  In **Desktop remoto** selezionare **Consenti agli utenti di connettersi in remoto al computer**.  
  
5.  Scegliere **OK**.  
  
## Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)