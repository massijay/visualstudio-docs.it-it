---
title: "Funzione SccUninitialize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUninitialize"
helpviewer_keywords: 
  - "Funzione SccUninitialize"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione SccUninitialize
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione Elimina le allocazioni o le connessioni aperte create da una precedente chiamata al [SccInitialize](../extensibility/sccinitialize-function.md) in preparazione per l'arresto di plug\-in del controllo del codice sorgente.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] Il puntatore alla struttura di contesto plug\-in del controllo di origine creati nel [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|La pulizia completata.|  
  
## Note  
 Il plug\-in del controllo del codice sorgente è responsabile per la preparazione di chiusura e di liberare la memoria allocata del plug\-in per la struttura di contesto. La funzione viene chiamata una volta per ogni istanza specifica di un plug\-in. Una chiamata al [SccInitialize](../extensibility/sccinitialize-function.md) precede questa chiamata. Nessun progetto può essere ancora aperto al momento della chiamata a `SccUninitialize`.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)