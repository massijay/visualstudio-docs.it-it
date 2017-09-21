---
title: "Funzione SccHistory | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "Funzione SccHistory"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Funzione SccHistory
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di visualizzare la cronologia dei file specificati.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parametri  
 `pvContext`  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 `hWnd`  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 `nFiles`  
 \[in\] Numero di file specificato per il `lpFileName` matrice.  
  
 `lpFileName`  
 \[in\] Matrice di nomi completi di file.  
  
 `fOptions`  
 \[in\] Flag di comando \(attualmente non utilizzato\).  
  
 `pvOptions`  
 \[in\] Opzioni specifiche plug\-in controllo sorgente.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Cronologia delle versioni è stata ottenuta correttamente.|  
|SCC\_I\_RELOADFILE|Il controllo del codice sorgente modificato effettivamente il file su disco durante il recupero della cronologia \(ad esempio, per ottenere una versione precedente\), in modo l'IDE deve caricare questo file.|  
|SCC\_E\_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_OPNOTSUPPORTED|Il controllo del codice sorgente non supporta questa operazione.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_PROJNOTOPEN|Il progetto non sia stata aperta.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato. Impossibile ottenere la cronologia dei file.|  
  
## Note  
 Il plug\-in del controllo del codice sorgente è possibile visualizzare una finestra di dialogo per visualizzare la cronologia di ogni file, utilizzando `hWnd` come la finestra padre. In alternativa, il testo facoltativo output callback funzione fornita per il [SccOpenProject](../extensibility/sccopenproject-function.md) può essere utilizzato, se è supportata.  
  
 Si noti che in determinate circostanze, il file in corso l'analisi potrebbe cambiare durante l'esecuzione di questa chiamata. Ad esempio, il [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] comando cronologia offre all'utente la possibilità di ottenere una versione precedente del file. In tal caso, il controllo origine plug\-in restituisce `SCC_I_RELOAD` per avvisare l'IDE ed è necessario ricaricare il file.  
  
> [!NOTE]
>  Se il plug\-in del controllo del codice sorgente non supporta questa funzione per una matrice di file, è possibile visualizzare solo la cronologia di file per il primo file.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)