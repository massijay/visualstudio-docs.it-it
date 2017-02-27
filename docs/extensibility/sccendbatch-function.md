---
title: "Funzione SccEndBatch | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "Funzione SccEndBatch"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Funzione SccEndBatch
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione è concluso un batch di operazioni di controllo codice sorgente. Questi batch non possono essere nidificati.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### Parametri  
 Nessuno.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Batch di operazioni conclude correttamente.|  
|SCC\_E\_UNKNOWNERROR|Errore non specificato.|  
  
## Note  
 Batch di controllo di origine utilizzati per eseguire le stesse operazioni di controllo di origine in più progetti o più contesti. Batch consente di eliminare le finestre di dialogo ridondanti dall'esperienza utente durante un'operazione batch. Il [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e `SccEndBatch` funzione vengono utilizzati come una coppia per indicare l'inizio e fine di un'operazione. Non possono essere annidate.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)