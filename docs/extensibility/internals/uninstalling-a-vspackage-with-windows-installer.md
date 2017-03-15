---
title: "Disinstallazione di un package VS con Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti, la disinstallazione"
  - "Package VS, disinstallazione"
  - "la disinstallazione di VSPackage"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Disinstallazione di un package VS con Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella maggior parte, Windows Installer possibile disinstallare solo per il pacchetto Visual Studio "annullamento" sia uguale a quello per installare il pacchetto Visual Studio. Le azioni personalizzate illustrate in [Comandi devono essere eseguiti dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md) deve essere eseguito dopo una disinstallazione anche. Poiché si verificano le chiamate a devenv.exe appena prima dell'azione standard InstallFinalize per l'installazione e disinstallazione, le voci della tabella CustomAction e InstallExecuteSequence rappresentano entrambi i casi.  
  
> [!NOTE]
>  Eseguire `devenv /setup` dopo la disinstallazione di un pacchetto MSI.  
  
 Come regola generale, se si aggiungono le azioni personalizzate a un pacchetto Windows Installer, è necessario gestire tali azioni durante la disinstallazione e il rollback. Se si aggiungono azioni personalizzate per registrare automaticamente il pacchetto Visual Studio, ad esempio, è necessario aggiungere azioni personalizzate per annullare la registrazione, troppo.  
  
> [!NOTE]
>  È possibile che un utente di installare il pacchetto Visual Studio e quindi disinstallare le versioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con cui è stato integrato. È possibile garantire che la disinstallazione del VSPackage funziona in tale scenario, eliminando le azioni personalizzate che eseguono il codice con dipendenze su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Gestione delle condizioni di avvio in fase di disinstallazione  
 L'azione standard LaunchConditions legge le righe della tabella per mostrare errore LaunchCondition messaggi se non vengono soddisfatte le condizioni. Come condizioni di avvio vengono generalmente utilizzate per garantire che siano soddisfatti i requisiti di sistema, in genere, è possibile ignorare le condizioni di avvio durante la disinstallazione aggiungendo la condizione, `NOT Installed`, alla riga della tabella LaunchCondition LaunchConditions.  
  
 In alternativa è possibile aggiungere `OR Installed` per avviare le condizioni che non sono importanti durante la disinstallazione. Questo garantisce che la condizione sarà sempre true durante la disinstallazione e pertanto non verrà visualizzato il messaggio di errore di condizione di avvio.  
  
> [!NOTE]
>  `Installed` la proprietà di che Windows Installer imposta quando viene rilevato che il pacchetto Visual Studio sia già installato nel sistema.  
  
## Vedere anche  
 [Windows Installer](http://msdn.microsoft.com/it-it/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)