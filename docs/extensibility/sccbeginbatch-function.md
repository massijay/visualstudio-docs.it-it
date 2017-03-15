---
title: "Funzione SccBeginBatch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "Funzione SccBeginBatch"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione SccBeginBatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione avvia una sequenza di batch di operazioni di controllo codice sorgente. Il [SccEndBatch](../extensibility/sccendbatch-function.md) verrà chiamato per terminare il batch. Questi batch non possono essere nidificati.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### Parametri  
 Nessuno.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Batch di operazioni iniziata correttamente.|  
|SCC\_E\_UNKNOWNERROR|Errore non specificato.|  
  
## Note  
 Batch di controllo di origine utilizzati per eseguire le stesse operazioni tra più progetti o più contesti. Batch consente di eliminare le finestre di dialogo progetto ridondanti dall'esperienza utente durante un'operazione batch. Il `SccBeginBatch` \(funzione\) e [SccEndBatch](../extensibility/sccendbatch-function.md) vengono utilizzati come una coppia di funzioni per indicare l'inizio e fine di un'operazione. Non possono essere annidate.`SccBeginBatch` imposta un flag che indica che un'operazione batch è in corso.  
  
 Mentre è in corso un'operazione batch, il plug\-in del controllo del codice sorgente deve presentare al massimo una finestra di dialogo per qualsiasi domanda all'utente e applicano la risposta da questa finestra di dialogo tutte le operazioni successive.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)