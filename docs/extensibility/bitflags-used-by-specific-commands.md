---
title: "Flag di bit utilizzati dai comandi specifici | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plug-in, flag di bit utilizzati dai comandi specifici controllo del codice sorgente"
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Flag di bit utilizzati dai comandi specifici
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Impostando uno o più bit in un singolo valore, è possibile modificare il comportamento di un numero di funzioni nell'API di plug\-in controllo di origine. Questi valori sono noti come flag di bit. Il flag di bit diversi utilizzati dall'API dei plug\-in controllo di origine sono descritti in questa sezione, raggruppati per la funzione che li utilizza.  
  
## Estratto Flag  
 Questo flag può essere impostato per entrambi i [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenere il file estratto.|  
  
## Aggiungere contrassegni  
 Questi flag vengono utilizzati dal [SccAdd](../extensibility/sccadd-function.md).  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|È previsto il plug\-in del controllo del codice sorgente per rilevare automaticamente se il file è di tipo testo o binario.|  
|`SCC_FILETYPE_TEXT`|0x01|Tipo di file è testo.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo di file è binario. **Note:**  `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` si escludono a vicenda. Impostare uno o nessuno.|  
|`SCC_ADD_STORELATEST`|0x02|Archiviare solo l'ultima versione \(non delta\).|  
  
## Flag di confronto  
 Il [SccDiff](../extensibility/sccdiff-function.md) utilizza questi flag per definire l'ambito di un'operazione diff. Il `SCC_DIFF_QD_xxx` si escludono a vicenda. Se viene specificato uno di essi, alcun feedback visivo non è concessa. In un "diff veloce" \(QD\), il plug\-in non determina come il file è diverso, solo se è diverso. Se nessuno di questi flag viene specificati, "diff visual" viene eseguita; le differenze tra file dettagliate vengono calcolate e visualizzate. QD richiesto non è supportata, il plug\-in si sposta in avanti quello più adatto. Ad esempio, se l'IDE richiede un checksum e il plug\-in non è supportata, non del plug\-in un contenuto full controllare \(comunque molto più velocemente una rappresentazione visiva\).  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorare le differenze.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorare le differenze di spazi vuoti. **Note:**  Il `SCC_DIFF_IGNORECASE` e `SCC_DIFF_IGNORESPACE` flag sono facoltativi flag di bit.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD confrontando l'intero contenuto del file.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD dal valore di checksum.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD dall'indicatore di data\/ora di file.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Questa è una maschera consente di controllare tutti i flag di bit QD. Non deve essere passato in una funzione. il flag di bit QD tre si escludono a vicenda. QD non significa sempre visualizzare alcuna interfaccia utente.|  
  
## Flag PopulateList  
 Questo flag viene utilizzato il [SccPopulateList](../extensibility/sccpopulatelist-function.md) nel `fOptions` parametro.  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|L'IDE passa directory, non i file.|  
  
## Flag PopulateDirList  
 Questi flag vengono utilizzati dal [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) nel `fOptions` parametro.  
  
|Valore dell'opzione|Valore|Descrizione|  
|-------------------------|------------|-----------------|  
|SCC\_PDL\_ONELEVEL|0x0000|Esaminare un solo livello di directory per le directory \(questo è il valore predefinito\).|  
|SCC\_PDL\_RECURSIVE|0x0001|In modo ricorsivo, esaminare tutte le directory in ogni directory specificata.|  
|SCC\_PDL\_INCLUDEFILES|0x0002|Includere i nomi di file nel processo di analisi.|  
  
## Flag OpenProject  
 Questi flag vengono utilizzati dal [SccOpenProject](../extensibility/sccopenproject-function.md) nel `dwFlags` parametro.  
  
|Valore dell'opzione|Valore|Descrizione|  
|-------------------------|------------|-----------------|  
|SCC\_OP\_CREATEIFNEW|0x00000001L|Se il progetto non esiste nel controllo del codice sorgente, è necessario crearla. Se non viene impostato questo flag, la richiesta utente di progetto da creare \(a meno che non `SCC_OP_SILENTOPEN` flag è specificato\).|  
|SCC\_OP\_SILENTOPEN|0x00000002L|Non chiedere conferma all'utente di creare un progetto. restituire `SCC_E_UNKNOWNPROJECT`.|  
  
## Ottenere flag  
 Questi flag vengono utilizzati dal [SccGet](../extensibility/sccget-function.md) e [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|L'IDE passa le directory, non i file: ottenere tutti i file in tali directory.|  
|`SCC_GET_RECURSIVE`|0x00000002L|L'IDE passa directory: ottenere queste directory e tutte le sottodirectory.|  
  
## Valori nOption  
 Questi flag vengono utilizzati dal [SccSetOption](../extensibility/sccsetoption-function.md) nel `nOption` parametro.  
  
|Flag|Valore|Descrizione|  
|----------|------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Impostare lo stato della coda di eventi.|  
|`SCC_OPT_USERDATA`|0x00000002L|Specificare i dati utente per `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L'IDE in grado di gestire Annulla|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Impostare un callback per le modifiche al nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Disabilitare l'estrazione dell'interfaccia utente plug\-in origine controllo e non si imposta la directory di lavoro.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Aggiungere il sistema di controllo per specificare una directory di lavoro. Provare a condividere il progetto associato, se è un discendente diretto.|  
  
## dwVal flag di bit  
 Questi flag vengono utilizzati dal [SccSetOption](../extensibility/sccsetoption-function.md) nel `dwVal` parametro.  
  
|Flag|Valore|Descrizione|Utilizzato da `nOption` valore|  
|----------|------------|-----------------|------------------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Sospende l'attività di coda di eventi.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Attiva la registrazione della coda di eventi.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|L 0|\(Impostazione predefinita\) Non possiede alcuna modalità di annullamento; plug\-in è necessario specificare se si desidera.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|L 1|IDE gestisce Annulla.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|L 0|\(Impostazione predefinita\) OK per estrarre dal plug\-in interfaccia utente. directory di lavoro è impostata.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|L 1|Nessun plug\-in estrazione dell'interfaccia utente, alcuna directory di lavoro.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)