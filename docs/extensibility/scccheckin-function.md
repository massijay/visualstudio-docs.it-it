---
title: Funzione SccCheckin | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e8bfa87246bc866a251951e4700b796d833dd63f
ms.lasthandoff: 02/22/2017

---
# <a name="scccheckin-function"></a>Funzione SccCheckin
Questa funzione controlla in precedenza i file estratti al sistema di controllo di origine, le modifiche e la creazione di una nuova versione. Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da archiviare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in del controllo di origine.  
  
 hWnd  
 [in] Handle di finestra IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file selezionati da archiviare.  
  
 lpFileNames  
 [in] Matrice di nomi di percorso completo dei file da archiviare.  
  
 lpComment  
 [in] Commento da applicare a ogni file selezionati da archiviare. Si tratta di `NULL` se il controllo del codice sorgente del plug-in una richiesta per un commento.  
  
 Opzioni  
 [in] Flag di comando, i valori validi sono 0 o `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Opzioni specifiche plug-in controllo del codice sorgente.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|I file è stato estratto correttamente.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC_E_NONSPECIFICERROR|Errore non specificato. File non è stato archiviato.|  
|SCC_E_NOTCHECKEDOUT|L'utente non ha estratto il file, in modo che non può archiviarla.|  
|SCC_E_CHECKINCONFLICT|Archiviazione non può essere eseguita perché:<br /><br /> -Un altro utente ha archiviato anticipo e `bAutoReconcile` è false.<br /><br /> -oppure-<br /><br /> -L'unione automatica non può essere eseguita (ad esempio, quando i file sono binari).|  
|SCC_E_VERIFYMERGE|File è stato unito automatico ma non è stato archiviato attesa di verifica dell'utente.|  
|SCC_E_FIXMERGE|File è stato unito automatico ma non è stato archiviato a causa di un conflitto di tipo merge che deve essere risolti manualmente.|  
|SCC_E_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC_I_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricata.|  
|SCC_E_FILENOTEXIST|File locale non trovato.|  
  
## <a name="remarks"></a>Note  
 Il commento si applica a tutti i file da archiviare. L'argomento commento può essere un `null` stringa, nel qual caso il plug-in del controllo del codice sorgente può chiedere all'utente per una stringa di commento per ogni file.  
  
 Il `fOptions` argomento può essere assegnato il valore di `SCC_KEEP_CHECKEDOUT` flag per indicare l'obiettivo dell'utente di archiviare il file ed estrarlo nuovamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)
