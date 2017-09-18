---
title: "POPLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "Funzione di callback POPLISTFUNC"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo callback viene fornito per il [SccPopulateList](../extensibility/sccpopulatelist-function.md) dall'IDE e viene utilizzato il plug\-in del controllo del codice sorgente per aggiornare un elenco di file o directory \(anche fornito per il `SccPopulateList` funzione\).  
  
 Quando un utente sceglie il **ottenere** comando nell'IDE, l'IDE visualizza una casella di riepilogo di tutti i file che l'utente può ottenere. Sfortunatamente, l'IDE non conosce l'esatto elenco di tutti i file che è possibile che venga visualizzato all'utente; solo il plug\-in dispone di questo elenco. Se altri utenti aggiungere file al progetto di controllo del codice sorgente, dovrebbero essere visualizzati nell'elenco di questi file, ma l'IDE non sa su di essi. L'IDE compila un elenco dei file che ritiene che l'utente può ottenere. Prima di questo elenco viene visualizzato all'utente, viene chiamato il [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` fornendo il controllo del codice sorgente del plug\-nella possibilità di aggiungere ed eliminare file dall'elenco.  
  
## Signature  
 Il plug\-in del controllo del codice sorgente consente di modificare l'elenco chiama una funzione con il seguente prototipo implementato IDE:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## Parametri  
 pvCallerData  
 Il `pvCallerData` parametro passato dal chiamante \(IDE\) per il [SccPopulateList](../extensibility/sccpopulatelist-function.md). Il plug\-in del controllo del codice sorgente deve presupporre alcuna informazione sul contenuto di questo parametro.  
  
 fAddRemove  
 Se `TRUE`, `lpFileName` è un file che deve essere aggiunti all'elenco di file. Se `FALSE`, `lpFileName` è un file che deve essere eliminato dall'elenco di file.  
  
 nStatus  
 Stato di `lpFileName` \(una combinazione del `SCC_STATUS` bits, vedere [Codice di stato file](../extensibility/file-status-code-enumerator.md) per informazioni dettagliate\).  
  
 lpFileName  
 Percorso completo della directory il nome del file per aggiungere o eliminare dall'elenco.  
  
## Valore restituito  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`TRUE`|Il plug\-in possono continuare a chiamare questa funzione.|  
|`FALSE`|Si è verificato un problema sul lato di IDE \(ad esempio, un timeout della situazione di memoria\). Il plug\-in deve interrompere l'operazione.|  
  
## Note  
 Per ogni file che il plug\-in del controllo del codice sorgente per aggiungere o eliminare dall'elenco dei file, viene chiamata questa funzione, passando il `lpFileName`. Il `fAddRemove` flag indica un nuovo file da aggiungere all'elenco o un vecchio file da eliminare. Il `nStatus` parametro fornisce lo stato del file. Quando il plug\-in del controllo del codice sorgente ha terminato di aggiunta ed eliminazione di file, viene restituito dal [SccPopulateList](../extensibility/sccpopulatelist-function.md) chiamare.  
  
> [!NOTE]
>  Il `SCC_CAP_POPULATELIST` bit funzionalità è necessaria per Visual Studio.  
  
## Vedere anche  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Codice di stato file](../extensibility/file-status-code-enumerator.md)