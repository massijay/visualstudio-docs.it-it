---
title: "Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office"
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
  - "sicurezza [sviluppo per Office in Visual Studio], risoluzione dei problemi"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Risoluzione dei problemi relativi alla sicurezza delle soluzioni Office
  In questo argomenti sono contenuti suggerimenti per la risoluzione di problemi comuni che possono verificarsi durante l'applicazione di misure di protezione alle soluzioni Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Le soluzioni attendibili non possono essere installate dai siti con restrizioni  
 Gli utenti non possono installare una soluzione da un percorso Web se il sito Web è elencato nell'area dei siti con restrizioni di Internet Explorer.  anche se la soluzione è firmata con un certificato attendibile.  
  
 L'URL del manifesto di distribuzione può essere suddiviso in categorie in una delle cinque aree:  
  
-   Risorse del computer  
  
-   Internet  
  
-   Intranet locale  
  
-   Siti attendibili  
  
-   Siti con restrizioni  
  
 Se il percorso del manifesto di distribuzione è stato assegnato all'area dei siti con restrizioni, in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non viene eseguita l'installazione della soluzione.  Se il percorso è conosciuto e può essere ritenuto attendibile, l'utente può rimuovere il percorso dall'area dei siti con restrizioni e la soluzione può essere installata.  Per informazioni sulla gestione delle aree , vedere [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774) \(informazioni in lingua inglese\).  
  
## Le soluzioni non possono essere installate da condivisioni di file di rete o da percorsi Web quando nei sistemi in cui è stato installato Internet Explorer 7 o la Sicurezza avanzata di Internet Explorer  
 Internet Explorer enhanced la configurazione della sicurezza \(IEESC\) in Windows Server 2003 e superiore e Internet Explorer 7 e superiore, limita notevolmente la possibilità di utenti di spostarsi Internet.  Quando gli utenti tentano di installare soluzioni Office da una condivisione file di rete o da un percorso web, è possibile che venga visualizzato il messaggio di errore seguente: “Le funzionalità personalizzate in questa applicazione non funzioneranno perché il certificato utilizzato per firmare il manifesto di distribuzione per *Nome soluzione* non è attendibile.  Per ulteriori informazioni, contattare l'amministratore".  
  
 Con IEESC e Internet Explorer 7 o versione successiva, se l'url del manifesto di distribuzione è suddivisa in categorie nell'area Internet, il manifesto deve disporre di un certificato da un editore attendibile o la soluzione non può essere installata.  Nei sistemi in cui IEESC non è presente, il comportamento predefinito consiste nel richiedere all'utente finale di prendere una decisione sull'attendibilità.  
  
 Per gestire l'effetto di IEESC e Internet Explorer 7 e superiore, identificare i siti Web e i percorsi universali di \(UNC\) la convenzione di denominazione che se vengono attendibili e aggiungere a una delle aree di sicurezza attendibili \(Intranet locale o siti Attendibili\). Per informazioni su come gestire le aree, vedere [Editore attendibile di ClickOnce di configurazione](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  