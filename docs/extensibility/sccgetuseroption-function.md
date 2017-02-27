---
title: "Funzione SccGetUserOption | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "Funzione SccGetUserOption"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione SccGetUserOption
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione recupera un'ampia gamma di opzioni specifiche dell'utente.  
  
## Sintassi  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 nOption  
 \[in\] Opzione da recuperare \(per le opzioni possibili, vedere la sezione Osservazioni\).  
  
 lpVal  
 \[out\] Valore associato all'opzione.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Opzione è stata recuperata correttamente.|  
|SCC\_E\_OPNOTSUPPORTED|Opzione non è supportata.|  
|SCC\_E\_NONSPECIFICERROR|Si è verificato un errore non specificato.|  
  
## Note  
 Le opzioni seguenti sono supportate da questo comando:  
  
|Opzione User|Descrizione|  
|------------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se l'utente desidera controllare la versione locale di file.`lpVal` viene assegnato `SCC_USEROPT_COLV_YES` \(utente desidera estrarre i file locali\) o `SCC_USEROPT_COLV_NO`.|  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Codici di errore](../extensibility/error-codes.md)