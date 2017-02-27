---
title: "Funzione SccCloseProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCloseProject"
helpviewer_keywords: 
  - "Funzione SccCloseProject"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Funzione SccCloseProject
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione chiude un progetto, contrassegna la fine di una determinata sessione.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### Parametri  
 pvContext  
 La struttura di contesto plug\-in del controllo di origine.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Il progetto è stato chiuso.|  
|SCC\_E\_PROJNOTOPEN|Non è aperto alcun progetto.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato.|  
  
## Note  
 Il [SccOpenProject](../extensibility/sccopenproject-function.md) viene sempre chiamato prima che questa funzione. Seguita da una chiamata a una chiamata a questa funzione il `SccOpenProject` funzione o [SccUninitialize](../extensibility/sccuninitialize-function.md), che termina la connessione per il controllo del codice sorgente completamente.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)