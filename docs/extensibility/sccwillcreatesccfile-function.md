---
title: "Funzione SccWillCreateSccFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccWillCreateSccFile"
helpviewer_keywords: 
  - "Funzione SccWillCreateSccFile"
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione SccWillCreateSccFile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione determina se il controllo del codice sorgente del plug\-in supporta la creazione di MSSCCPRJ. File SCC per ogni file specificati.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 nFiles  
 \[in\] Il numero di nomi di file nel `lpFileNames` oltre la lunghezza della matrice di `pbSccFiles` matrice.  
  
 lpFileNames  
 \[in\] Una matrice di nomi di file completo per controllare \(matrice deve essere allocata dal chiamante\).  
  
 pbSccFiles  
 \[in, out\] Matrice in cui archiviare i risultati.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Operazione completata.|  
|SCC\_E\_INVALIDFILEPATH|Uno dei percorsi nella matrice non è valido.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato.|  
  
## Note  
 Questa funzione viene chiamata con un elenco di file per determinare se il plug\-in del controllo del codice sorgente fornisce il supporto nel MSSCCPRJ. File SCC per ogni file specificati \(per ulteriori informazioni sul MSSCCPRJ. File di controllo del codice sorgente, vedere [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)\). Plug\-in del controllo codice sorgente è possibile dichiarare se hanno la possibilità di creare MSSCCPRJ. File SCC dichiarando `SCC_CAP_SCCFILE` durante l'inizializzazione. Il plug\-in restituisce `TRUE` o `FALSE` per ogni file nel `pbSccFiles` matrice per indicare che il file specificato hanno MSSCCPRJ. Supporto di controllo del codice sorgente. Se il plug\-in restituisce un codice di riuscita tramite la funzione, vengono accettati i valori nella matrice restituita. In caso di errore, la matrice viene ignorata.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md)