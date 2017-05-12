---
title: "Concessione dell&#39;attendibilit&#224; alle soluzioni Office mediante gli elenchi di inclusione"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "autorizzazioni [sviluppo per Office in Visual Studio]"
  - "elenchi di inclusione [sviluppo per Office in Visual Studio], informazioni sugli elenchi di inclusione"
  - "sicurezza [sviluppo per Office in Visual Studio], elenchi di inclusione"
  - "elenchi di inclusione [sviluppo per Office in Visual Studio]"
ms.assetid: 6dae0128-435b-4fa1-aed9-73e728fdcacf
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Concessione dell&#39;attendibilit&#224; alle soluzioni Office mediante gli elenchi di inclusione
  Gli elenchi di inclusione consentono agli utenti di concedere l'attendibilità alle soluzioni Office firmate con un certificato che identifica l'editore. Gli elenchi di inclusione sono specifici dell'utente e possono essere usati per le personalizzazioni a livello di documento e per i componenti aggiuntivi VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Quando un utente avvia una soluzione Microsoft Office a cui non è stata concessa l'attendibilità per tale utente, verrà richiesto all'utente di prendere una decisione di sicurezza con una richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Se l'utente decide di concedere l'attendibilità alla soluzione, viene eseguita la personalizzazione e l'utente non riceverà più richieste successivamente.  
  
## Elenco di inclusione e Windows Installer  
 L'installazione di soluzioni Office nella directory Programmi con Windows Installer richiede diritti di amministratore. Per le soluzioni Office nella directory Programmi, il Runtime di Visual Studio Tools per Office non controlla più l'elenco di inclusione perché alle soluzioni Office sono già state concesse le autorizzazioni FullTrust.  
  
## Richiesta di attendibilità ClickOnce  
 Con l'implementazione di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] per le soluzioni Office, gli amministratori possono configurare il livello di richiesta di attendibilità. In particolare, è possibile abilitare o disabilitare la funzionalità di richiesta di attendibilità oppure richiedere un certificato attendibile. Questa configurazione viene eseguita usando una chiave del Registro di sistema che controlla l'accesso all'elenco di inclusione.  
  
 Se la funzionalità di richiesta di attendibilità è disabilitata, il sistema consente di installare solo le soluzioni che dispongono di un certificato attendibile e noto. Se il livello di richiesta di attendibilità prevede la richiesta di un certificato Authenticode, la soluzione deve essere firmata con un certificato fornito da un'autorità nota, non necessariamente collegato con una catena di trust a un'autorità radice attendibile \(cioè un certificato attendibile\). Se la funzionalità di richiesta di attendibilità è attiva, la soluzione può essere firmata con un certificato con un'identità sconosciuta. In questo scenario, la decisione sull'attendibilità viene presa dall'utente finale e per installare una soluzione è sufficiente un certificato temporaneo.  
  
 Per altre informazioni, vedere [Procedura: configurare la sicurezza dell'elenco di inclusione](../vsto/how-to-configure-inclusion-list-security.md) e la tabella 2, intitolata Prompting Level Registry Key Value Launch Effects, dell'articolo relativo alla [configurazione di editori attendibili ClickOnce](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Struttura dell'elenco di inclusione  
 Una voce valida di un elenco di inclusione presenta due parti: un percorso al manifesto della distribuzione e la chiave pubblica usata per firmare la soluzione. Le soluzioni che vengono aggiunte all'elenco di inclusione vengono considerate attendibili. Quando la soluzione Office viene eseguita, l'applicazione di Office confronta la chiave pubblica contenuta nell'elenco di inclusione con la chiave di firma contenuta nel manifesto della distribuzione allo scopo di verificare se la soluzione in esecuzione corrisponde alla versione originale ritenuta attendibile.  
  
## Vedere anche  
 [Concessione dell'attendibilità alle soluzioni Office](../vsto/granting-trust-to-office-solutions.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  