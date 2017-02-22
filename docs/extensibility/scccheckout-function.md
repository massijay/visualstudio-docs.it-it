---
title: "Funzione SccCheckout | Microsoft Docs"
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
  - "SccCheckout"
helpviewer_keywords: 
  - "Funzione SccCheckout"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccCheckout
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dato un elenco di nomi completi dei file, questa funzione li estrae nell'unità locale. Il commento si applica a tutti i file estratti. L'argomento commento può essere un `null` stringa.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccCheckout (  
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
 \[in\] Numero di file selezionati per l'estrazione.  
  
 lpFileNames  
 \[in\] Matrice di nomi di percorso completo del file da estrarre.  
  
 lpComment  
 \[in\] Commento da applicare a ogni file selezionati venga estratti.  
  
 Opzioni  
 \[in\] Flag di comando \(vedere [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)\).  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Check\-out è stato completato.|  
|SCC\_E\_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. Il file non è stato estratto.|  
|SCC\_E\_ALREADYCHECKEDOUT|L'utente ha già estratto il file.|  
|SCC\_E\_FILEISLOCKED|Il file è bloccato, che non consentono la creazione di nuove versioni.|  
|SCC\_E\_FILEOUTEXCLUSIVE|Un altro utente ha eseguito un'estrazione esclusiva su questo file.|  
|SCC\_I\_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)