---
title: "Funzione SccDiff | Microsoft Docs"
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
  - "SccDiff"
helpviewer_keywords: 
  - "Funzione SccDiff"
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccDiff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di visualizzare \(o facoltativamente appena Cerca\) le differenze tra il file corrente \(nel disco locale\) e la relativa ultima versione archiviata nell'origine del sistema di controllo.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpFileName  
 \[in\] Nome del file per il quale viene richiesta la differenza.  
  
 Opzioni  
 \[in\] Flag di comando. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|La versione di copia e il server di lavoro sono identici.|  
|SCC\_I\_FILESDIFFERS|La copia di lavoro è diverso dalla versione di controllo del codice sorgente.|  
|SCC\_I\_RELOADFILE|Un progetto o il file deve essere ricaricata.|  
|SCC\_E\_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. differenza tra i file non è stato ottenuto.|  
|SCC\_E\_FILENOTEXIST|Non è stato trovato il file locale.|  
  
## Note  
 Questa funzione ha due scopi diversi. Per impostazione predefinita, viene visualizzato un elenco di modifiche in un file. Il plug\-in del controllo del codice sorgente verrà visualizzata la relativa finestra, in qualsiasi formato sceglie, per visualizzare le differenze tra file dell'utente su disco e la versione più recente del file di controllo del codice sorgente.  
  
 In alternativa, l'IDE semplicemente necessario determinare se un file è stato modificato. L'IDE, ad esempio, potrebbe essere necessario determinare se è possibile estrarre un file senza informare l'utente. In tal caso, l'IDE passa il `SCC_DIFF_CONTENTS` flag. Il plug\-in del controllo del codice sorgente deve controllare il file su disco, byte per byte, in base al file sorgente e restituire un valore che indica se i due file sono diversi, senza alcuna visualizzazione all'utente.  
  
 Ottimizzare le prestazioni, il plug\-in del controllo del codice sorgente può utilizzare un'alternativa in base a un checksum o di un timestamp anziché il confronto byte per byte indicato `SCC_DIFF_CONTENTS`: queste forme di confronto sono ovviamente più veloce ma meno affidabile. Non tutti i sistemi di controllo di origine supportino questi metodi di confronto alternativo e il plug\-in potrebbe essere necessario eseguire il fallback a un confronto di contenuto. Tutti plug\-in controllo codice sorgente, è necessario come minimo, supporta un confronto di contenuto.  
  
> [!NOTE]
>  I flag di differenza rapida si escludono a vicenda. È possibile non passare alcun flag, ma non è valido passare contemporaneamente più di uno.`SCC_DIFF_QUICK_DIFF`, che è una maschera che combina tutti i flag, può essere utilizzato per verificare, ma non deve mai essere passato come parametro.  
  
|`fOption`|Significato|  
|---------------|-----------------|  
|SCC\_DIFF\_IGNORECASE|Confronto tra maiuscole e minuscole \(può essere usato per differenza rapido o visual\).|  
|SCC\_DIFF\_IGNORESPACE|Ignora gli spazi vuoti \(può essere usato per differenza rapido o visual\).|  
|SCC\_DIFF\_QD\_CONTENTS|Confronta automaticamente il file, byte per byte.|  
|SCC\_DIFF\_QD\_CHECKSUM|Confronta automaticamente il file tramite un checksum quando è supportata. Se non è supportato, esegue il fallback a un confronto del contenuto.|  
|SCC\_DIFF\_QD\_TIME|Confronta automaticamente il file tramite il relativo timestamp quando è supportata. Se non è supportato, esegue il fallback a un confronto del contenuto.|  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)