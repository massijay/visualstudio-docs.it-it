---
title: "Funzione SccGet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGet"
helpviewer_keywords: 
  - "Funzione SccGet"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione SccGet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione recupera una copia di uno o più file per la visualizzazione e la compilazione ma non per la modifica. Nella maggior parte dei sistemi, i file vengono contrassegnati come di sola lettura.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccGet(  
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
 \[in\] La struttura di contesto del plug\-in del controllo del codice sorgente.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 nFiles  
 \[in\] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi completi di file da recuperare.  
  
 Opzioni  
 \[in\] Flag di comando \(`SCC_GET_ALL`, `SCC_GET_RECURSIVE`\).  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Esito positivo dell'operazione get.|  
|SCC\_E\_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC\_E\_FILEISCHECKEDOUT|Impossibile ottenere il file che l'utente ha estratto.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NOSPECIFIEDVERSION|Versione non valida o data\/ora specificati.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. file non è stato sincronizzato.|  
|SCC\_I\_OPERATIONCANCELED|Operazione annullata prima del completamento.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|  
  
## Note  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi dei file da recuperare. Se l'IDE passa il flag `SCC_GET_ALL`, ciò significa che gli elementi in `lpFileNames` non sono file, ma le directory e che tutti i file nel controllo del codice sorgente nella directory specificata devono essere recuperate.  
  
 Il `SCC_GET_ALL` flag può essere combinato con il `SCC_GET_RECURSIVE` flag per recuperare tutti i file nella directory specificata e tutte le sottodirectory anche.  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` non deve mai essere passato senza `SCC_GET_ALL`. Si noti inoltre che se directory C:\\A e C:\\A\\B vengono passati una ricorsiva get, C:\\A\\B e tutte le relative sottodirectory verranno effettivamente recuperate due volte. È responsabilità dell'IDE, e non il controllo origine del plug\-in, per assicurarsi che i duplicati, ad esempio questo si trovino dalla matrice.  
  
 Infine, anche se un controllo del codice sorgente del plug\-in specificato il `SCC_CAP_GET_NOUI` flag durante l'inizializzazione, che indica che non dispone di un'interfaccia utente per un comando Get, questa funzione può comunque essere chiamata dall'IDE per recuperare i file. Il flag indica semplicemente che l'IDE non viene visualizzata una voce di menu Get e che il plug\-in non è previsto fornire l'interfaccia utente.  
  
## La ridenominazione e SccGet  
 Situazione: un utente estrae un file, ad esempio, txt e lo modifica. Prima txt possono essere archiviati, un secondo utente rinomina txt in b. txt nel database di controllo di origine, estrae b. txt, apporta alcune modifiche al file e archivia il file. Il primo utente desidera le modifiche apportate dall'utente secondo pertanto il primo utente rinomina la versione locale di un file txt in b. txt e non un'operazione get sul file. Tuttavia, la cache locale che tiene traccia dei numeri di versione pensa ancora la prima versione di a. txt viene archiviata in locale e quindi controllo del codice sorgente non può risolvere le differenze.  
  
 Esistono due modi per risolvere questa situazione in cui la cache locale delle versioni di controllo di origine viene sincronizzata con il database del controllo del codice sorgente:  
  
1.  Non consentire la ridenominazione di un file nel database di controllo di origine che è attualmente estratto.  
  
2.  Eseguire l'equivalente di "eliminazione precedente" seguita da "Aggiungi nuovo". L'algoritmo seguente è un modo per eseguire questa operazione.  
  
    1.  Chiamare il [SccQueryChanges](../extensibility/sccquerychanges-function.md) funzione per apprendere la ridenominazione di a. txt in b. txt nel database di controllo di origine.  
  
    2.  Rinominare txt locale in b. txt.  
  
    3.  Chiamare il `SccGet` funzione per txt e b. txt.  
  
    4.  Perché txt non esiste nel database di controllo di origine, viene eliminata la cache della versione locale delle informazioni sulla versione txt mancante.  
  
    5.  Il file b. txt estratto viene unito con il contenuto del file locale b. txt.  
  
    6.  Il file aggiornato b. txt possa essere archiviato.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)