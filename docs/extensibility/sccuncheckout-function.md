---
title: "Funzione SccUncheckout | Microsoft Docs"
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
  - "SccUncheckout"
helpviewer_keywords: 
  - "Funzione SccUncheckout"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccUncheckout
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di annullare un'operazione di estrazione precedente, ripristinando in questo modo il contenuto del file selezionato o di file allo stato precedente l'estrazione. Tutte le modifiche apportate al file dopo l'estrazione andranno perse.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 nFiles  
 \[in\] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi di percorso completo del file per il quale annullare l'estrazione.  
  
 Opzioni  
 \[in\] Flag di comando \(non utilizzato\).  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Annullamento estrazione riuscito.|  
|SCC\_E\_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. Annulla estrazione non riuscita.|  
|SCC\_E\_NOTCHECKEDOUT|L'utente non dispone di file viene estratto.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_PROJNOTOPEN|Non è stato aperto il progetto dal controllo del codice sorgente.|  
|SCC\_I\_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
  
## Note  
 Dopo questa operazione, il `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` flag verranno cancellati per i file in cui è stato eseguito l'annullamento dell'estrazione.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)