---
title: "Funzione SccEnumChangedFiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "Funzione SccEnumChangedFiles"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione SccEnumChangedFiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dato un elenco di file locali, questa funzione determina quali file sono diversi rispetto alle versioni corrispondenti nel database del controllo del codice sorgente.  
  
## Sintassi  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 cFiles  
 \[in\] Numero di nomi di file specificati nel `lpFileNames` matrice. Specifica inoltre le dimensioni di `plIsFileDifferent` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi di file locale da verificare.  
  
 plIsFileDifferent  
 \[in, out\] Matrice di valori che indica lo stato di differenza di ogni file \(matrice deve avere almeno `cFiles` voci\). Diverso da zero indica che il file è diverso.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Operazione completata correttamente.|  
|SCC\_UNSPECIFIEDERROR|Errore generico.|  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)