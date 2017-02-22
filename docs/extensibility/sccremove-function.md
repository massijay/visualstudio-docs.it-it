---
title: "Funzione SccRemove | Microsoft Docs"
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
  - "SccRemove"
helpviewer_keywords: 
  - "Funzione SccRemove"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccRemove
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione Elimina i file dal sistema di controllo di origine.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 \[in\] Matrice di nomi di percorso completo del file da rimuovere.  
  
 lpComment  
 \[in\] Il commento da applicare a ogni file da rimuovere.  
  
 Opzioni  
 \[in\] Flag di comando \(non utilizzato\).  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Rimozione è stata completata.|  
|SCC\_E\_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC\_E\_ISCHECKEDOUT|Impossibile rimuovere il file perché un utente è attualmente estratto.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. file non è stato rimosso.|  
|SCC\_I\_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
  
## Note  
 Questa funzione rimuove i file dal sistema di controllo di origine ma non vengono eliminati dal disco rigido locale dell'utente.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)