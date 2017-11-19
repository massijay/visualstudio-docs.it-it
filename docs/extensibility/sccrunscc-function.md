---
title: Funzione SccRunScc | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRunScc
helpviewer_keywords: SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9ac82ac0363428ade1b6010a9060e15284db224
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="sccrunscc-function"></a>SccRunScc (funzione)
Questa funzione richiama lo strumento di amministrazione di controllo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 pvContext  
 [in] La struttura di contesto plug-in controllo di origine.  
  
 hWnd  
 [in] Un handle di finestra dell'IDE che il plug-in controllo del codice sorgente è possibile utilizzare come un elemento padre per eventuali finestre di dialogo che fornisce.  
  
 nFiles  
 [in] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 [in] Matrice di nomi di file selezionato.  
  
## <a name="return-value"></a>Valore restituito  
 Implementazione di plug-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|SCC_OK|Lo strumento di amministrazione di controllo di origine è stato richiamato correttamente.|  
|SCC_I_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il controllo del codice sorgente.|  
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC_E_CONNECTIONFAILURE|Impossibile connettersi al sistema di controllo di origine.|  
|SCC_E_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC_E_NONSPECIFICERROR|Errore non specifico.|  
  
## <a name="remarks"></a>Note  
 Questa funzione consente al chiamante di accedere all'intera gamma di funzionalità del sistema di origine tramite uno strumento di amministrazione esterne. Se il controllo del codice sorgente non dispone di alcuna interfaccia utente, il plug-in controllo del codice sorgente può implementare un'interfaccia per eseguire funzioni amministrative necessarie.  
  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi di file per i file attualmente selezionati. Se supporta lo strumento di amministrazione, l'elenco di file consente di preselezionato file nell'interfaccia di amministrazione. in caso contrario, l'elenco può essere ignorato.  
  
 Questa funzione in genere viene richiamata quando l'utente seleziona il **avviare \<Server di controllo di origine >** dal **File** -> **controllo del codice sorgente** dal menu. Questo **avviare** opzione di menu può essere sempre disabilitata o anche nascoste impostando una voce del Registro di sistema. Vedere [procedura: installare un plug-in controllo origine](../extensibility/internals/how-to-install-a-source-control-plug-in.md) per informazioni dettagliate. Questa funzione viene chiamata solo se [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il `SCC_CAP_RUNSCC` bit funzionalità (vedere [flag di capacità](../extensibility/capability-flags.md) per informazioni dettagliate su questo e gli altri bit funzionalità).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API plug-in controllo di origine](../extensibility/source-control-plug-in-api-functions.md)   
 [Procedura: installare un plug-in controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Flag di capacità](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)