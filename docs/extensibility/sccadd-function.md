---
title: "Funzione SccAdd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAdd"
helpviewer_keywords: 
  - "Funzione SccAdd"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Funzione SccAdd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di aggiungere nuovi file per il controllo del codice sorgente.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 nFiles  
 \[in\] Numero di file selezionati da aggiungere al progetto corrente specificato nella `lpFileNames` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi locali completi del file da aggiungere.  
  
 lpComment  
 \[in\] Il commento da applicare a tutti i file da aggiungere.  
  
 pfOptions  
 \[in\] Matrice di flag di comando, fornite in un singolo file.  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Completata l'operazione di aggiunta.|  
|SCC\_E\_FILEALREADYEXISTS|Il file selezionato è già in controllo del codice sorgente.|  
|SCC\_E\_TYPENOTSUPPORTED|Il tipo di file \(ad esempio, binario\) non è supportato dal sistema di controllo di origine.|  
|SCC\_E\_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. aggiungere non eseguita.|  
|SCC\_I\_OPERATIONCANCELED|L'operazione è stata annullata prima del completamento.|  
|SCC\_I\_RELOADFILE|Un progetto o il file deve essere ricaricata.|  
|SCC\_E\_FILENOTEXIST|File locale non trovato.|  
  
## Note  
 La consueta `fOptions` vengono sostituite seguito da una matrice, `pfOptions`, con uno `LONG` opzione specifica per ogni file. Questo avviene perché il tipo di file può variare da un file in un file.  
  
> [!NOTE]
>  Non è possibile specificare sia `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` Opzioni per lo stesso file, ma è possibile specificare nessuno. L'impostazione non è la stessa impostazione `SCC_FILETYPE_AUTO`, nel qual caso il controllo origine plug\-in rileva automaticamente il tipo di file.  
  
 Di seguito è riportato l'elenco di flag utilizzati nella `pfOptions` matrice:  
  
|Opzione|Valore|Significato|  
|-------------|------------|-----------------|  
|SCC\_FILETYPE\_AUTO|0x00|Il plug\-in del controllo del codice sorgente deve rilevare il tipo di file.|  
|SCC\_FILETYPE\_TEXT|0x01|Indica un file di testo ASCII.|  
|SCC\_FILETYPE\_BINARY|0x02|Indica un tipo di file diverso da testo ASCII.|  
|SCC\_ADD\_STORELATEST|0x04|Archivia solo la copia più recente del file, nessun delta.|  
|SCC\_FILETYPE\_TEXT\_ANSI|0x08|Considera il file come testo ANSI.|  
|SCC\_FILETYPE\_UTF8|0x10|Considera il file come testo Unicode in formato UTF8.|  
|SCC\_FILETYPE\_UTF16LE|0x20|Considera il file come testo Unicode in formato UTF16 Little Endian formato.|  
|SCC\_FILETYPE\_UTF16BE|0x40|Considera formattare il file come testo Unicode in formato UTF16 Big Endian.|  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)