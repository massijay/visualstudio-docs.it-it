---
title: "Errore: il sito utilizza un indirizzo IP | Microsoft Docs"
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
  - "vs.debug.error.webdbg_siteusesipaddress"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, errori dell'applicazione Web"
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: il sito utilizza un indirizzo IP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo errore si verifica quando il debugger tenta di connettersi automaticamente a un'applicazione Web che utilizza un indirizzo IP  ed è dovuto alla selezione di **Usa indirizzo IP specifico** anziché **Identificazione sito Web** in IIS.  
  
 Per il funzionamento della connessione automatica, occorre creare il progetto con l'indirizzo IP specifico piuttosto che con il semplice nome del computer.  In caso contrario, il debugger modificherà il nome del computer in localhost causando l'esito negativo dell'invio del verbo debug a IIS.  
  
### Per correggere l'errore  
  
1.  Utilizzare la connessione manuale, scegliendo **Connetti a processo** dal menu Debug.  
  
     —oppure—  
  
2.  Modificare l'impostazione **Identificazione sito Web IIS**.  
  
## Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)