---
title: "Funzione SccDirQueryInfo | Microsoft Docs"
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
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "Funzione SccDirQueryInfo"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccDirQueryInfo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione esamina un elenco di directory completo per il relativo stato corrente.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 nDirs  
 \[in\] Il numero di directory selezionato deve essere sottoposto a query.  
  
 lpDirNames  
 \[in\] Matrice di percorsi completi delle directory in cui eseguire la query.  
  
 lpStatus  
 \[in, out\] Una struttura di matrice per il controllo del codice sorgente del plug\-in per restituire i flag di stato \(vedere [Codice di stato di directory](../extensibility/directory-status-code-enumerator.md) per informazioni dettagliate\).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|La query è riuscita.|  
|SCC\_E\_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Errore non specificato.|  
  
## Note  
 La funzione riempie la matrice restituita con una maschera di bit dal `SCC_DIRSTATUS` famiglia \(vedere [Codice di stato di directory](../extensibility/directory-status-code-enumerator.md)\), una voce per ogni directory specificata. La matrice di stato viene allocata dal chiamante.  
  
 L'IDE utilizza questa funzione prima di una directory viene rinominata per verificare la directory di controllo del codice sorgente eseguendo una query se dispone di un progetto corrispondente. Se la directory non è incluso nel controllo del codice sorgente, l'IDE fornirà l'avviso appropriato all'utente.  
  
> [!NOTE]
>  Se un plug\-in del controllo del codice sorgente sceglie di non implementare uno o più dei valori di stato, non è implementata bit deve essere impostato su zero.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Codice di stato di directory](../extensibility/directory-status-code-enumerator.md)