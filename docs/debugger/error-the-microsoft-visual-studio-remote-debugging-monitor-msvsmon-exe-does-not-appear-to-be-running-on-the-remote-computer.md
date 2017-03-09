---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo messaggio di errore indica che Visual Studio non ha trovato l'istanza corretta di Visual Studio Remote Debugging Monitor nel computer remoto. Per il funzionamento del debug remoto, è necessario che Visual Studio Remote Debugging Monitor sia installato. Per informazioni sul download e la configurazione del debugger remoto, vedere [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
> [!IMPORTANT]
>  Se si ritiene di aver ricevuto il messaggio a causa di un bug del prodotto, segnalare il problema a [Invia smile](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md) di Visual Studio. Per ottenere ulteriore assistenza, vedere [Comunicazioni con Microsoft](../ide/talk-to-us.md) per le modalità di contatto di Microsoft.  
  
## Il messaggio è stato visualizzato durante il debug in Visual Studio 2010 o versioni precedenti  
 Se la versione di Visual Studio in uso è Visual Studio 2010 o versioni precedenti, l'errore potrebbe essere visualizzato perché non è abilitata la condivisione di file e stampanti. Per altre informazioni su questo problema, fare riferimento alla versione Visual Studio 2010 di questa documentazione: [Errore: Microsoft Visual Studio Remote Debugging Monitor \(MSVSMON.EXE\) non sembra essere in esecuzione sul computer remoto. \- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## Il messaggio è stato visualizzato durante un debug locale  
 Se si riceve questo messaggio durante un debug locale, il problema potrebbe essere causato dal software antivirus o da un firewall di terze parti. Visual Studio è un'applicazione a 32 bit, quindi usa la versione a 64 bit del debugger remoto per eseguire il debug delle applicazioni a 64 bit. I due processi comunicano usando la rete locale nel computer locale. Il traffico resta all'interno del computer, ma è possibile che un software per la sicurezza di terze parti blocchi la comunicazione.  
  
 Le sezioni seguenti elencano altri motivi per cui potrebbe essere visualizzato questo messaggio e le soluzioni disponibili.  
  
## Il computer remoto non è raggiungibile  
 Provare a eseguire il [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) del computer remoto. Se non risponde al ping, neanche gli strumenti remoti potranno connettersi. Provare a riavviare il computer remoto, altrimenti assicurarsi che sia configurato correttamente sulla rete.  
  
## La versione del debugger remoto non corrisponde alla versione di Visual Studio  
 La versione di Visual Studio in esecuzione in locale deve corrispondere alla versione di Remote Debugging Monitor in esecuzione nel computer remoto. Per risolvere questo problema, scaricare e installare la versione corrispondente di Remote Debugging Monitor. Andare nell'[Area download](http://www.microsoft.com/en-us/download) per trovare la versione corretta per il debugger remoto.  
  
## Il computer locale e quello remoto hanno modalità di autenticazione diverse  
 Il computer locale e quello remoto devono usare la stessa modalità di autenticazione. Per risolvere questo problema, assicurarsi che entrambi i computer usino la stessa modalità di autenticazione. Per altre informazioni sulle modalità di autenticazione, vedere [Panoramica di Autenticazione di Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## Il debugger remoto è in esecuzione con un altro account utente  
 Per risolvere il problema, usare uno dei metodi seguenti:  
  
-   Arrestare il debugger remoto e riavviarlo con l'account in uso nel computer locale.  
  
-   Avviare il debugger remoto dalla riga di comando con il parametro **\/allow \<username\>**: `msvsmon /allow <username@computer>`  
  
-   È possibile aggiungere l'utente alle autorizzazioni del debugger remoto, nella finestra del debugger remoto, **Strumenti\/Autorizzazioni**.  
  
-   Se i metodi descritti in precedenza non sono applicabili, è possibile consentire a tutti gli utenti di eseguire il debug remoto. Nella finestra del debugger remoto, andare nella finestra di dialogo **Strumenti\/Opzioni**. Se si seleziona **Nessuna autenticazione**, è possibile selezionare **Consenti debug da parte di qualsiasi utente**. Tuttavia, questa opzione va usata solo se non sono disponibili le altre o se ci si trova in una rete privata.  
  
## Il firewall nel computer remoto non consente le connessioni in ingresso nel debugger remoto  
 Il firewall nel computer Visual Studio e il firewall nel computer remoto devono essere configurati per consentire la comunicazione tra Visual Studio e il debugger remoto. Per informazioni sulle porte usate dal debugger remoto, vedere [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md). Per informazioni sulla configurazione del firewall di Windows, vedere [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## Il software antivirus sta bloccando le connessioni  
 Il software antivirus di Windows consente le connessioni del debugger remoto, mentre altri software antivirus di terze parti potrebbero bloccarle. Controllare la documentazione del software antivirus per scoprire come consentire queste connessioni.  
  
## I criteri di sicurezza di rete bloccano la comunicazione tra il computer remoto e Visual Studio  
 Esaminare la sicurezza della rete per assicurarsi che non blocchi la comunicazione. Per altre informazioni sui criteri di sicurezza di rete di Windows, vedere [Gestione della sicurezza](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## La rete è troppo occupata per supportare il debug remoto  
 Provare a eseguire il debug remoto in un altro momento oppure pianificare il lavoro sulla rete per un altro orario.  
  
## Altre informazioni  
 Per ottenere ulteriore assistenza sul debugger remoto, inclusi opzioni della riga di comando, aprire quanto segue in un browser:  
  
 **res:\/\/C:\\Program%20Files\\Microsoft%20Visual%20Studio%2014.0\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm**  
  
## Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)