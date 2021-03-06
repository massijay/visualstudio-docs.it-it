---
title: Funzione SccAddFilesFromSCC | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFilesFromSCC
helpviewer_keywords: SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1764bfc503e25860326b1910c432edcf95c8f21c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC (funzione)
Questa funzione consente di aggiungere un elenco di file dal controllo del codice sorgente al progetto attualmente aperto.  
  
## <a name="syntax"></a>Sintassi  
  
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
  
#### <a name="parameters"></a>Parametri  
 pContext  
 [in] Il puntatore di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 lpUser  
 [in, out] Il nome utente (fino a SCC_USER_SIZE, incluso il carattere di terminazione null).  
  
 lpAuxProjPath  
 [in, out] Ausiliario stringa di identificazione del progetto (fino a `SCC_PRJPATH_`dimensioni, incluso il carattere di terminazione null).  
  
 cFiles  
 [in] Numero di file specificato da `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Matrice di nomi di file da aggiungere al progetto corrente.  
  
 lpDestination  
 [in] Il percorso di destinazione in cui i file devono essere scritti.  
  
 lpComment  
 [in] Il commento da applicare a ogni file da aggiungere.  
  
 pbResults  
 [in, out] Matrice di flag di set per indicare l'esito positivo (diverso da zero o TRUE) o negativo (zero o FALSE) per ogni file (dimensione della matrice deve essere almeno `cFiles` long).  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Progetto non è aperto.|  
|SCC_E_OPNOTPERFORMED|Connessione non è presente nello stesso progetto, come specificato da`lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Utente non è autorizzato ad aggiornare il database.|  
|SCC_E_NONSPECIFICERROR|Errore sconosciuto.|  
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)