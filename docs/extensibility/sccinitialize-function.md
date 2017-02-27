---
title: "Funzione SccInitialize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "Funzione SccInitialize"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Funzione SccInitialize
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di inizializzare il plug\-in del controllo del codice sorgente e fornisce funzionalità e i limiti per l'ambiente di sviluppo integrato \(IDE\).  
  
## Sintassi  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### Parametri  
 `ppvContext`  
 \[in\] Il plug\-in del controllo del codice sorgente è possibile inserire un puntatore alla struttura relativo contesto qui.  
  
 `hWnd`  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 `lpCallerName`  
 \[in\] Il nome del programma di chiamata del plug\-in di controllo del codice sorgente.  
  
 `lpSccName`  
 \[in, out\] Il buffer in cui il plug\-in del controllo del codice sorgente inserisce il proprio nome \(non superiore a `SCC_NAME_LEN`\).  
  
 `lpSccCaps`  
 \[out\] Restituisce il controllo del codice sorgente il flag di capacità del plug\-in.  
  
 `lpAuxPathLabel`  
 \[in, out\] Il buffer in cui il plug\-in del controllo del codice sorgente inserisce una stringa che descrive il `lpAuxProjPath` restituito dal parametro il [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(non superiore a `SCC_AUXLABEL_LEN`\).  
  
 `pnCheckoutCommentLen`  
 \[out\] Restituisce la lunghezza massima consentita per un commento di estrazione.  
  
 `pnCommentLen`  
 \[out\] Restituisce la lunghezza massima consentita per gli altri commenti.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Inizializzazione di controllo di origine ha avuto esito positivo.|  
|SCC\_E\_INITIALIZEFAILED|Impossibile inizializzare il sistema.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire l'operazione specificata.|  
|SCC\_E\_NONSPECFICERROR|Errore non specificato. controllo del codice sorgente non è stato inizializzato.|  
  
## Note  
 Questa funzione viene chiamata l'IDE al primo caricamento del plug\-in controllo del codice sorgente. In questo modo l'IDE passare a determinate informazioni, ad esempio il nome del chiamante, il plug\-in. L'IDE inoltre consente di ottenere determinate informazioni, quali la lunghezza massima consentita per le funzionalità del plug\-in e i commenti.  
  
 Il `ppvContext` punta a un `NULL` puntatore. Il plug\-in del controllo del codice sorgente può allocare una struttura per l'utilizzo e archiviare un puntatore a tale struttura in `ppvContext`. L'IDE passerà il puntatore per qualsiasi altra funzione API VSSCI, consentendo il plug\-in sono disponibili informazioni di contesto senza ricorrere a un archivio globale e per supportare più istanze di plug\-in. Questa struttura deve essere deallocata quando il [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.  
  
 Il `lpCallerName` e `lpSccName` i parametri consentono l'IDE e il plug\-in del controllo del codice sorgente per lo scambio di nomi. Questi nomi possono essere utilizzati semplicemente per distinguere tra più istanze, o possono essere effettivamente visualizzate nei menu o finestre di dialogo.  
  
 Il `lpAuxPathLabel` parametro è una stringa utilizzata come un commento per identificare il percorso del progetto ausiliarie che viene archiviato nel file di soluzione e passato il controllo del codice sorgente plug\-in una chiamata al [SccOpenProject](../extensibility/sccopenproject-function.md).[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] utilizza la stringa "progetto di Visual SourceSafe:"; altri plug\-in del controllo origine deve evitare l'utilizzo di questa particolare stringa.  
  
 Il `lpSccCaps` parametro fornisce il controllo del codice sorgente del plug\-in una posizione in cui archiviare i flag di bit che indica le capacità del plug\-in. \(Per un elenco completo dei flag di bit di funzionalità, vedere [Flag di capacità](../extensibility/capability-flags.md)\). Ad esempio, se i piani di plug\-in per scrivere i risultati in una funzione di callback fornito dal chiamante, il plug\-in necessario impostare la funzionalità di bit SCC\_CAP\_TEXTOUT. Questo potrebbe segnalare l'IDE per creare una finestra per i risultati di controllo di versione.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Flag di capacità](../extensibility/capability-flags.md)