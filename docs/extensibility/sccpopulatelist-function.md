---
title: "Funzione SccPopulateList | Microsoft Docs"
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
  - "SccPopulateList"
helpviewer_keywords: 
  - "Funzione SccPopulateList"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccPopulateList
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione aggiorna un elenco di file per un comando di controllo di origine specifica e fornisce lo stato del controllo di origine in tutti i file specificati.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 n Ncomando  
 \[in\] Il comando di controllo di origine che verrà applicato a tutti i file di `lpFileNames` matrice \(vedere [Codice di comando](../extensibility/command-code-enumerator.md) per un elenco di possibili comandi\).  
  
 nFiles  
 \[in\] Numero di file di `lpFileNames` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi di file noti all'IDE.  
  
 pfnPopulate  
 \[in\] La funzione di callback da chiamare per aggiungere e rimuovere i file di IDE \(vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate\).  
  
 pvCallerData  
 \[in\] Valore che deve essere passato invariato per la funzione di callback.  
  
 lpStatus  
 \[in, out\] Matrice per il plug\-in per restituire i flag di stato per ogni file di controllo del codice sorgente.  
  
 Opzioni  
 \[in\] Flag di comando \(vedere la sezione "flag PopulateList" di [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) per informazioni dettagliate\).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Operazione completata.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato.|  
  
## Note  
 Questa funzione esamina l'elenco di file per lo stato corrente. Usa il `pfnPopulate` funzione di callback per notificare al chiamante quando un file non corrispondono ai criteri per il `nCommand`. Ad esempio, se il comando è `SCC_COMMAND_CHECKIN` e un file nell'elenco non è stato estratto, quindi la richiamata viene utilizzata per segnalare al chiamante. In alcuni casi, il plug\-in del controllo del codice sorgente potrebbero essere presenti altri file che potrebbero far parte del comando e aggiungerli. In questo modo, ad esempio, un utente di Visual Basic per estrarre un file con estensione bmp che viene utilizzato il proprio progetto ma non viene visualizzato nel file di progetto Visual Basic. Un utente sceglie il **ottenere** comando nell'IDE. L'IDE verrà visualizzato un elenco di tutti i file che ritiene che l'utente può ottenere, ma prima della visualizzazione elenco, il `SccPopulateList` funzione viene chiamata per verificare che sia aggiornato l'elenco da visualizzare.  
  
## Esempio  
 L'IDE compila un elenco di file che ritiene che l'utente può ottenere. Prima di visualizzare l'elenco, viene chiamato il `SccPopulateList` di funzione, consentendo il controllo del codice sorgente del plug\-in per aggiungere ed eliminare i file dall'elenco. Il plug\-in modifica l'elenco di chiamando la funzione di richiamata specificata \(vedere [POPLISTFUNC](../extensibility/poplistfunc.md) Per ulteriori dettagli\).  
  
 Il plug\-in continua a chiamare il `pfnPopulate` funzione, che aggiunge ed elimina i file, fino a quando non è terminato e lo restituisce il `SccPopulateList` \(funzione\). L'IDE può quindi visualizzare il relativo elenco. Il `lpStatus` matrice rappresenta tutti i file nell'elenco originale passato dall'IDE. Il plug\-in compila lo stato di tutti questi file oltre a rendere utilizza la funzione di callback.  
  
> [!NOTE]
>  Un plug\-in del controllo del codice sorgente è sempre possibile semplicemente restituire immediatamente da questa funzione, senza modificare l'elenco. Se un plug\-in implementa questa funzione, è possibile che questo impostando il `SCC_CAP_POPULATELIST` flag di bit di funzionalità nella prima chiamata per il [SccInitialize](../extensibility/sccinitialize-function.md). Per impostazione predefinita, il plug\-in necessario presupporre sempre che tutti gli elementi passati sono file. Tuttavia, se l'IDE imposta il `SCC_PL_DIR` flag nel `fOptions` parametro, tutti gli elementi passati devono essere considerati directory. Il plug\-in deve aggiungere tutti i file che appartengono nelle directory. L'IDE non passerà mai in una combinazione di file e directory.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [Flag di bit utilizzati dai comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)   
 [Codice di comando](../extensibility/command-code-enumerator.md)