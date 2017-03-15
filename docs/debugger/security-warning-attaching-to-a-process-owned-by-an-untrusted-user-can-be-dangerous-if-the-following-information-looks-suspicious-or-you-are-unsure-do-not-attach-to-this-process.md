---
title: "Avviso di sicurezza: pu&#242; essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo. | Microsoft Docs"
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
  - "vs.debug.attachsecuritywarning"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Avviso di sicurezza: pu&#242; essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo di avviso viene visualizzata quando si stabilisce una connessione a un processo che contiene codice parzialmente attendibile o codice di proprietà di un utente non attendibile subito prima che abbia luogo la connessione.  Un processo non attendibile contenente codice malware può danneggiare il computer durante l'esecuzione del debug.  Se si ritiene che il processo non sia attendibile, è opportuno fare clic su **Annulla** per impedire il debug.  
  
 Per eliminare l'avviso durante il debug di uno scenario legittimo, chiudere Visual Studio e impostare il valore di questa chiave del Registro di sistema su 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, quindi riavviare Visual Studio.  Dopo aver completato il debug dello scenario, reimpostare il valore su 0 e riavviare Visual Studio.  
  
 Tra gli utenti attendibili sono inclusi quello che esegue il debug e un set di utenti standard comunemente definiti nei computer in cui è installato .NET Framework, ad esempio `aspnet`, `localsystem`, `networkservice` e `localservice`.  
  
## Elenco UIElement  
 Nome  
 Nome dell'assembly di cui è richiesto il debug  
  
 Utente  
 Utente corrente  
  
 Connetti  
 Scegliere questo pulsante per connettersi al processo e proseguire il debug  
  
 Non connettersi  
 Non connettersi al processo  
  
## Vedere anche  
 [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)