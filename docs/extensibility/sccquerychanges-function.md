---
title: "Funzione SccQueryChanges | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryChanges"
helpviewer_keywords: 
  - "Funzione SccQueryChanges"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccQueryChanges
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione enumera un elenco di file, che fornisce informazioni sulle modifiche ai nomi per ogni file tramite una funzione di callback specificato.  
  
## Sintassi  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 nFiles  
 \[in\] Numero di file in `lpFileNames` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi di file per cui ottenere informazioni.  
  
 pfnCallback  
 \[in\] Funzione di callback da chiamare per ogni nome di file nell'elenco \(vedere [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) per informazioni dettagliate\).  
  
 pvCallerData  
 \[in\] Valore che verrà passato invariato per la funzione di callback.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Il processo di query completato.|  
|SCC\_E\_PROJNOTOPEN|Il progetto non è stato aperto nel controllo del codice sorgente.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC\_E\_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|  
  
## Note  
 Sottoposto a query per le modifiche sono per lo spazio dei nomi: in particolare, la ridenominazione, l'aggiunta e rimozione di un file.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Codici di errore](../extensibility/error-codes.md)