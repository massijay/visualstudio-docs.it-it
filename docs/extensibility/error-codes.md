---
title: "Codici di errore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "codici di errore, plug-in del controllo codice sorgente"
  - "origine plug-in del controllo, i codici di errore"
  - "errori [Visual Studio SDK]"
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Codici di errore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando una funzione API plug\-in controllo di origine restituisce un errore, si deve essere uno dei seguenti codici di errore. Tutti gli errori sono negativi, avvisi o i codici di errore informativo sono positivi, esito positivo è 0.  
  
|Codice di errore|Valore|Descrizione|  
|----------------------|------------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Plug\-in supporta l'aggiunta di file dal controllo del codice sorgente in due passaggi. Per altre informazioni, vedere [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Il file locale è diverso dal file nel database del controllo del codice sorgente \(ad esempio, [SccDiff](../extensibility/sccdiff-function.md) può restituire il valore\).|  
|`SCC_I_RELOADFILE`|5|File locale è stato modificato durante l'operazione di controllo di origine. l'IDE deve ricaricare il file se possibile.|  
|`SCC_I_FILENOTAFFECTED`|4|Il file non è interessato.|  
|`SCC_I_PROJECTCREATED`|3|Il progetto è stato creato durante l'operazione di controllo di origine \(ad esempio, durante una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md) quando `SCC_OP_CREATEIFNEW` flag è specificato\).|  
|`SCC_I_OPERATIONCANCELED`|2|Operazione annullata.|  
|`SCC_I_ADV_SUPPORT`|1|Plug\-in supporta opzioni avanzate per il comando specificato. Per altre informazioni, vedere [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Operazione completata.|  
|`SCC_E_INITIALIZEFAILED`|\-1|Errore: inizializzazione non riuscita.|  
|`SCC_E_UNKNOWNPROJECT`|\-2|Errore: progetto è sconosciuto.|  
|`SCC_E_COULDNOTCREATEPROJECT`|\-3|Errore: Impossibile creare progetto.|  
|`SCC_E_NOTCHECKEDOUT`|\-4|Errore: il file non estratto.|  
|`SCC_E_ALREADYCHECKEDOUT`|\-5|Errore: il file è già estratto.|  
|`SCC_E_FILEISLOCKED`|\-6|Errore: il file è bloccato.|  
|`SCC_E_FILEOUTEXCLUSIVE`|\-7|Errore: il file viene estratto in esclusiva.|  
|`SCC_E_ACCESSFAILURE`|\-8|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|`SCC_E_CHECKINCONFLICT`|\-9|Errore: si è verificato un conflitto durante l'archiviazione.|  
|`SCC_E_FILEALREADYEXISTS`|\-10|Errore: il file esiste già.|  
|`SCC_E_FILENOTCONTROLLED`|\-11|Errore: il file non è incluso nel controllo del codice sorgente.|  
|`SCC_E_FILEISCHECKEDOUT`|\-12|Errore: il file è estratto.|  
|`SCC_E_NOSPECIFIEDVERSION`|\-13|Errore: non è una versione specificata.|  
|`SCC_E_OPNOTSUPPORTED`|\-14|Errore: l'operazione non è supportata.|  
|`SCC_E_NONSPECIFICERROR`|\-15|Errore non specificato.|  
|`SCC_E_OPNOTPERFORMED`|\-16|L'errore, l'operazione non è stata eseguita.|  
|`SCC_E_TYPENOTSUPPORTED`|\-17|Errore: il tipo di file, ad esempio, binario, non è supportato dal sistema di controllo codice sorgente.|  
|`SCC_E_VERIFYMERGE`|\-18|File è stato unito automatico ma non è stato archiviato perché verifica dell'utente in sospeso.|  
|`SCC_E_FIXMERGE`|\-19|File è stato unito automatico ma non è stato archiviato a causa di un conflitto di tipo merge che deve essere risolti manualmente.|  
|`SCC_E_SHELLFAILURE`|\-20|Errore causato da un errore di shell.|  
|`SCC_E_INVALIDUSER`|\-21|Errore: l'utente non è valido.|  
|`SCC_E_PROJECTALREADYOPEN`|\-22|Errore: il progetto è già aperto.|  
|`SCC_E_PROJSYNTAXERR`|\-23|Errore di sintassi del progetto.|  
|`SCC_E_INVALIDFILEPATH`|\-24|Errore: il percorso del file non è valido.|  
|`SCC_E_PROJNOTOPEN`|\-25|Errore: il progetto non è aperto.|  
|`SCC_E_NOTAUTHORIZED`|\-26|Errore: l'utente non è autorizzato a eseguire questa operazione.|  
|`SCC_E_FILESYNTAXERR`|\-27|Errore di sintassi del file.|  
|`SCC_E_FILENOTEXIST`|\-28|L'errore, il file locale non esiste.|  
|`SCC_E_CONNECTIONFAILURE`|\-29|Errore: si è verificato un errore di connessione.|  
|`SCC_E_UNKNOWNERROR`|\-30|Errore sconosciuto.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|\-31|Operazione get in background è in corso.|  
  
## Macro fornite per il controllo rapido  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE) IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE) IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## Note  
 Tutte le funzioni API plug\-in controllo di origine \(ad eccezione di [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), e [SccDiff](../extensibility/sccdiff-function.md)\) dovrebbero avere esito positivo quando i file locali che vengono passati come argomenti non esistono nella cartella di lavoro. Ad esempio, l'IDE può inviare una chiamata al [SccCheckout](../extensibility/scccheckout-function.md) o [SccUncheckout](../extensibility/sccuncheckout-function.md) in un file che non esiste nella cartella di lavoro, ma esiste nel sistema di controllo di origine. Questa chiamata potrebbe avere esito positivo. Solo quando non esiste alcun file nella cartella di lavoro o nel sistema di controllo di origine la funzione dovrebbe avere esito negativo.  
  
 Alcune funzioni, ad esempio `SccAdd` e `SccCheckin`, in particolare deve restituire `SCC_E_FILENOTEXIST` quando il file nella cartella di lavoro non esiste. Altre funzioni devono avere esito positivo quando il file di lavoro non esiste, se le funzioni di operano su un nome file valido nel sistema di controllo di origine.  
  
 Il controllo del codice sorgente del plug\-in necessario non fare supposizioni sui privilegi su un file nella cartella di lavoro, anche se il plug\-in sono stati contrassegnati il file di sola lettura durante alcune operazioni. Un file nella cartella di lavoro può essere spostato, eliminato e modificato di fuori controllo del plug\-in.  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)