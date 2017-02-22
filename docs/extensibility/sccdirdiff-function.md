---
title: "Funzione SccDirDiff | Microsoft Docs"
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
  - "SccDirDiff"
helpviewer_keywords: 
  - "Funzione SccDirDiff"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccDirDiff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di visualizzare le differenze tra la directory corrente del disco di client e il progetto corrispondente nel controllo del codice sorgente.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpDirName  
 \[in\] Percorso completo della directory locale per il quale mostrano una differenza di visual.  
  
 dwFlags  
 \[in\] Flag di comando \(vedere la sezione Osservazioni sezione\).  
  
 pvOptions  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|La directory su disco è identico al progetto nel controllo del codice sorgente.|  
|SCC\_I\_FILESDIFFER|La directory su disco è diversa dal progetto nel controllo del codice sorgente.|  
|SCC\_I\_RELOADFILE|Un progetto o il file deve essere ricaricata.|  
|SCC\_E\_FILENOTCONTROLLED|La directory non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Errore non specificato.|  
|SCC\_E\_FILENOTEXIST|Impossibile trovare la directory locale.|  
  
## Note  
 Questa funzione viene utilizzata per indicare al controllo di origine del plug\-in da visualizzare all'utente un elenco delle modifiche in una directory specificata. Il plug\-in verrà visualizzata la relativa finestra, in un formato di propria scelta, per visualizzare le differenze tra la directory dell'utente su disco e il progetto corrispondente nel controllo della versione.  
  
 Se un confronto di plug\-in supporta di directory affatto, deve supportare il confronto delle directory in base a nome di file anche se non sono supportate le opzioni "diff veloce".  
  
|`dwFlags`|Interpretazione|  
|---------------|---------------------|  
|SCC\_DIFF\_IGNORECASE|Confronto tra maiuscole e minuscole \(può essere usato per diff veloce o visual\).|  
|SCC\_DIFF\_IGNORESPACE|Ignora gli spazi vuoti \(può essere usato per diff veloce o visual\).|  
|SCC\_DIFF\_QD\_CONTENTS|Se supportato dal plug\-in del controllo del codice sorgente, confronta automaticamente nella directory, byte per byte.|  
|SCC\_DIFF\_QD\_CHECKSUM|Se supportato dal plug\-in, in modo invisibile confronta la directory tramite un checksum o, se non è supportato, esegue il fallback a SCC\_DIFF\_QD\_CONTENTS.|  
|SCC\_DIFF\_QD\_TIME|Se supportato dal plug\-in, in modo invisibile confronta la directory tramite il relativo timestamp o, se non è supportato, esegue il fallback su SCC\_DIFF\_QD\_CHECKSUM o SCC\_DIFF\_QD\_CONTENTS.|  
  
> [!NOTE]
>  Questa funzione utilizza gli stessi flag di comando come il [SccDiff](../extensibility/sccdiff-function.md). Tuttavia, un plug\-in del controllo del codice sorgente è possibile scegliere di non supporta l'operazione "diff veloce" per le directory.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)