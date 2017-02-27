---
title: "Errore: il server Web &#232; stato bloccato e blocca il verbo DEBUG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.webdbg_debug_verb_blocked"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, errori dell'applicazione Web"
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Errore: il server Web &#232; stato bloccato e blocca il verbo DEBUG
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'accesso a un'applicazione Web o a un servizio Web XML non è riuscito in quanto è stato eseguito lo strumento di blocco IIS ed è stato installato e attivato URLScan.  Questa condizione impedisce la ricezione del verbo DEBUG da parte di IIS.  
  
 URLScan è uno strumento di sicurezza che viene utilizzato con lo strumento di blocco IIS per fornire agli amministratori di siti Web IIS la capacità di disattivare le funzioni non necessarie e limitare il tipo di richieste HTTP che verranno elaborate dal server.  Bloccando richieste HTTP specifiche, lo strumento di sicurezza URLScan impedisce a richieste potenzialmente dannose di raggiungere il server e causare danni.  
  
 Se l'applicazione viene eseguita in IIS 6.0 in Windows Server 2003, non è necessario eseguire lo strumento di blocco IIS perché IIS 6.0 fornisce la stessa funzionalità.  
  
### Per attivare il debug su un server Web con URLScan installato  
  
1.  Individuare il file Urlscan.ini.  In genere è presente in una directory simile a quella indicata di seguito.  
  
     C:\\WINNT\\System32\\Inetsrv\\urlscan  
  
2.  Creare una copia del file e assegnarvi il nome Urlscan.old.  
  
3.  Aprire la copia originale del file Urlscan.ini mediante il Blocco note o l'editore di testo desiderato.  
  
4.  In Urlscan.ini individuare la sezione \[AllowVerbs\].  Aggiungere DEBUG alla sezione \[AllowVerbs\].  Se è presente la stringa ;DEBUG nella sezione \[AllowVerbs\], e il punto e virgola per rimuovere il commento dal verbo.  
  
5.  Individuare la sezione \[DenyVerbs\].  Rimuovere DEBUG, se è presente nella sezione \[DenyVerbs\].  
  
6.  Salvare il file.  
  
7.  Riavviare il server o IIS.  
  
## Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Errore: il server Web non è in grado di trovare la risorsa richiesta](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)