---
title: "Funzione SccAddFilesFromSCC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFilesFromSCC"
helpviewer_keywords: 
  - "Funzione SccAddFilesFromSCC"
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Funzione SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di aggiungere un elenco di file dal controllo del codice sorgente per il progetto attualmente aperto.  
  
## Sintassi  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpUser  
 \[in, out\] Il nome utente \(fino a SCC\_USER\_SIZE, compreso il terminatore null\).  
  
 lpAuxProjPath  
 \[in, out\] Stringa ausiliaria che identifica il progetto \(fino a `SCC_PRJPATH_`dimensioni, compreso il terminatore null\).  
  
 cFiles  
 \[in\] Numero di file specificato da `lpFilePaths`.  
  
 lpFilePaths  
 \[in, out\] Matrice di nomi di file da aggiungere al progetto corrente.  
  
 lpDestination  
 \[in\] Il percorso di destinazione in cui i file devono essere scritti.  
  
 lpComment  
 \[in\] Il commento da applicare a ogni file da aggiungere.  
  
 pbResults  
 \[in, out\] Matrice di flag impostato per indicare esito positivo \(diverso da zero o TRUE\) o negativo \(zero o FALSE\) per ogni file \(dimensione della matrice deve essere almeno `cFiles` tempo\).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_E\_PROJNOTOPEN|Progetto non è aperto.|  
|SCC\_E\_OPNOTPERFORMED|Connessione non è presente nello stesso progetto, come specificato da `lpAuxProjPath.`|  
|SCC\_E\_NOTAUTHORIZED|Utente non è autorizzato ad aggiornare il database.|  
|SCC\_E\_NONSPECIFICERROR|Errore sconosciuto.|  
|SCC\_I\_RELOADFILE|Un progetto o il file deve essere ricaricata.|  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)