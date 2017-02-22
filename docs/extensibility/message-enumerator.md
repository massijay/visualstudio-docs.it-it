---
title: "Enumeratore di messaggio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "enumeratore di messaggio"
  - "origine plug-in del controllo, enumerazione messaggio"
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Enumeratore di messaggio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I flag seguenti vengono utilizzati per il `TEXTOUTPROC` funzione, che è una funzione di callback nell'IDE sono disponibili quando si chiama il [SccOpenProject](../extensibility/sccopenproject-function.md) \(vedere [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) per informazioni dettagliate sulla funzione di callback\).  
  
 Se l'IDE viene richiesto di annullare il processo, è possibile ottenere uno dei messaggi di annullamento. In questo caso, il controllo origine plug\-in utilizza `SCC_MSG_STARTCANCEL` per richiedere l'IDE per visualizzare il **Annulla** pulsante. Successivamente, è possibile inviare qualsiasi set di messaggi normali. Se uno di questi restituisce `SCC_MSG_RTN_CANCEL`, il plug\-in viene chiuso l'operazione e restituisce. Il plug\-in esegue inoltre il polling `SCC_MSG_DOCANCEL` periodicamente per determinare se l'utente ha annullato l'operazione. Quando tutte le operazioni vengono eseguite, o se l'utente ha annullato, invia il plug\-in `SCC_MSG_STOPCANCEL`. Il `SCC_MSG_INFO`, SCC\_MSG\_WARNING, e i tipi SCC\_MSG\_ERROR vengono utilizzati per i messaggi vengono visualizzati nell'elenco scorrevole dei messaggi.`SCC_MSG_STATUS` è un tipo speciale che indica che il testo da visualizzare in una barra di stato o l'area di visualizzazione temporanea. Non resta in modo permanente nell'elenco.  
  
## Sintassi  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## Membri  
 SCC\_MSG\_RTN\_CANCEL  
 Restituito dal callback per indicare di annullamento.  
  
 SCC\_MSG\_RTN\_OK  
 Restituito dal callback per continuare.  
  
 SCC\_MSG\_INFO  
 Messaggio è puramente informativo.  
  
 SCC\_MSG\_WARNING  
 Messaggio è un avviso.  
  
 SCC\_MSG\_ERROR  
 Messaggio indica un errore.  
  
 SCC\_MSG\_STATUS  
 Messaggio è destinato a barra di stato.  
  
 SCC\_MSG\_DOCANCEL  
 Nessun testo; Restituisce IDE `SCC_MSG_RTN_OK` o `SCC_MSG_RTN_CANCEL`.  
  
 SCC\_MSG\_STARTCANCEL  
 Avvia un ciclo di annullamento.  
  
 SCC\_MSG\_STOPCANCEL  
 Arresta il ciclo di annullamento.  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)