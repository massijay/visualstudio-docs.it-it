---
title: "Impossibile connettersi al processo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.unable2attach"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Impossibile connettersi al processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Impossibile connettersi al processo.Accesso negato per il componente del debugger che si trova sul server durante la connessione a questo computer.  
  
 Esistono due scenari comuni in cui viene generato questo errore:  
  
 **Scenario 1:** nel computer A è in esecuzione Windows XP.  Nel computer B è in esecuzione Windows Server 2003.  Il Registro di sistema del computer B contiene il seguente valore DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 L'utente 1 avvia una sessione Terminal Server \(sessione 1\) sul computer B e avvia un'applicazione gestita da tale sessione.  
  
 L'utente 2, che è amministratore su entrambi i computer, è connesso al computer A,  da cui cerca di connettersi a un'applicazione in esecuzione nella sessione 1 sul computer B.  
  
 **Scenario 2:** un utente è connesso a due computer, A e B, appartenenti allo stesso gruppo di lavoro e utilizza la stessa password per entrambi i computer.  Il debugger è in esecuzione sul computer A e sta tentando di eseguire la connessione a un'applicazione gestita in esecuzione sul computer B.  Nel computer A l'opzione **Accesso alla rete: modello di condivisione e sicurezza per gli account locali** è impostata su **Guest**.  
  
### Per risolvere lo scenario 1  
  
-   Eseguire il debugger e l'applicazione gestita con lo stesso nome account e password.  
  
### Per risolvere lo scenario 2  
  
1.  Fare clic sul pulsante **Start** e scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo fare doppio clic sull'icona **Strumenti di amministrazione**.  
  
3.  Nella finestra Strumenti di amministrazione fare doppio clic su **Criteri di sicurezza locali**.  
  
4.  Nella finestra Criteri di sicurezza locali selezionare **Criteri locali**.  
  
5.  Nella colonna **Criteri** fare doppio clic su **Accesso alla rete: modello di condivisione e sicurezza per gli account locali**.  
  
6.  Nella finestra di dialogo **Accesso alla rete: modello di condivisione e sicurezza per gli account locali** impostare la sicurezza locale su **Classico**, quindi scegliere **OK**.  
  
    > [!CAUTION]
    >  L'impostazione del modello di sicurezza su Classico può determinare l'accesso imprevisto a file condivisi e componenti DCOM.  In questo caso, un utente remoto può eseguire l'autenticazione con l'account utente locale anziché come Guest.  Se il nome utente e la password specificati dall'utente remoto coincidono con quelli dell'account locale, tale utente potrà accedere a qualsiasi cartella o oggetto DCOM condiviso.  Se si utilizza questo modello di sicurezza, assicurarsi che per tutti gli account utente sul computer siano impostate password complesse oppure configurare un'area di rete isolata per i computer coinvolti nelle operazioni di debug in modo da impedire l'accesso non autorizzato.  
  
7.  Chiudere tutte le finestre.  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)