---
title: "Message Codes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message codes"
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Message Codes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In ogni riga del messaggio mostrata in [Visualizzazione messaggi](../debugger/messages-view.md) è contenuto un codice 'P', 'S', 's' o 'R'.  Di seguito è riportato il significato di questi codici:  
  
|Codice|Significato|  
|------------|-----------------|  
|P|Il messaggio è stato inviato alla coda con la funzione **PostMessage**.  Non è disponibile nessuna informazione sulla disposizione finale del messaggio.|  
|S|Il messaggio è stato inviato con la funzione **SendMessage**.  Pertanto il mittente non riotterrà il controllo finché il ricevitore non elabora e restituisce il messaggio.  Il ricevitore può quindi passare nuovamente un valore restituito al mittente.|  
|s|Il messaggio è stato inviato, ma le impostazioni di sicurezza non consentono di accedere al valore restituito.|  
|R|Ogni riga 'S' dispone di una riga 'R' \(restituzione\) corrispondente in cui è elencato il valore restituito del messaggio.  Talvolta le chiamate al messaggio sono annidate, ovvero un gestore di messaggi invia un altro messaggio.|